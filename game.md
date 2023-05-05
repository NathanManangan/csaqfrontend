<html>
<head>
  <title>Basic Doodle Jump HTML Game</title>
  <meta charset="UTF-8">
  <style>
      html, body {xc
        height: 100%;  
        margin: 0;
      }  
      body {
        display: grid;
        text-align: center;
        vertical-align: center; 
        justify-content: center;
      }
      canvas {
        border: 2px solid #FF0000;
        background-color: #E6E6E6;
        border-radius: 10px;
        box-shadow: 0px 0px 10px #FF0000;
        display: block;
        margin: auto;
        height: 60%;
        width: 120%;
      }
  </style>
</head>
<body>
<canvas width="375" height="667" id="game"></canvas>
<script>
  const canvas = document.getElementById('game');
  const context = canvas.getContext('2d');
  const platformWidth = 65;
  const platformHeight = 20;
  const platformStart = canvas.height - 50;
  const gravity = 0.33;
  const drag = 0.3;
  const bounceVelocity = -12.5;
  let minPlatformSpace = 15;
  let maxPlatformSpace = 20;
  let platforms = [{
    x: canvas.width / 2 - platformWidth / 2,
    y: platformStart
  }];
  function random(min, max) {
    return Math.random() * (max - min) + min;
  }
  let y = platformStart;
  while (y > 0) {
    y -= platformHeight + random(minPlatformSpace, maxPlatformSpace);
    let x;
    do {
      x = random(25, canvas.width - 25 - platformWidth);
    } while (
      y > canvas.height / 2 &&
      x > canvas.width / 2 - platformWidth * 1.5 &&
      x < canvas.width / 2 + platformWidth / 2
    );
    platforms.push({ x, y });
  }
  const doodle = {
    width: 40,
    height: 60,
    x: canvas.width / 2 - 20,
    y: platformStart - 60,
    dx: 0,
    dy: 0
  };
  let playerDir = 0;
  let keydown = false;
  let prevDoodleY = doodle.y;
  function loop() {
    requestAnimationFrame(loop);
    context.clearRect(0,0,canvas.width,canvas.height);
    // apply gravity to doodle
    doodle.dy += gravity;
    // if doodle reaches the middle of the screen, move the platforms down
    // instead of doodle up to make it look like doodle is going up
    if (doodle.y < canvas.height / 2 && doodle.dy < 0) {
      platforms.forEach(function(platform) {
        platform.y += -doodle.dy;
      });
      // add more platforms to the top of the screen as doodle moves up
      while (platforms[platforms.length - 1].y > 0) {
        platforms.push({
          x: random(25, canvas.width - 25 - platformWidth),
          y: platforms[platforms.length - 1].y - (platformHeight + random(minPlatformSpace, maxPlatformSpace))
        })
        // add a bit to the min/max platform space as the player goes up
        minPlatformSpace += 0.5;
        maxPlatformSpace += 0.5;
        // cap max space
        maxPlatformSpace = Math.min(maxPlatformSpace, canvas.height / 2);
      }
    }
    else {
      doodle.y += doodle.dy;
    }
    // only apply drag to horizontal movement if key is not pressed
    if (!keydown) {
      if (playerDir < 0) {
        doodle.dx += drag;
        // don't let dx go above 0
        if (doodle.dx > 0) {
          doodle.dx = 0;
          playerDir = 0;
        }
      }
      else if (playerDir > 0) {
        doodle.dx -= drag;
        if (doodle.dx < 0) {
          doodle.dx = 0;
          playerDir = 0;
        }
      }
    }
    doodle.x += doodle.dx;
    // make doodle wrap the screen
    if (doodle.x + doodle.width < 0) {
      doodle.x = canvas.width;
    }
    else if (doodle.x > canvas.width) {
      doodle.x = -doodle.width;
    }
    // draw platforms
    context.fillStyle = 'green';
    platforms.forEach(function(platform) {
      context.fillRect(platform.x, platform.y, platformWidth, platformHeight);
      // make doodle jump if it collides with a platform from above
      if (
        // doodle is falling
        doodle.dy > 0 &&
        // doodle was previous above the platform
        prevDoodleY + doodle.height <= platform.y &&
        // doodle collides with platform
        // (Axis Aligned Bounding Box [AABB] collision check)
        doodle.x < platform.x + platformWidth &&
        doodle.x + doodle.width > platform.x &&
        doodle.y < platform.y + platformHeight &&
        doodle.y + doodle.height > platform.y
      ) {
        // reset doodle position so it's on top of the platform
        doodle.y = platform.y - doodle.height;
        doodle.dy = bounceVelocity;
      }
    });
    // draw doodle
    context.fillStyle = 'yellow';
    context.fillRect(doodle.x, doodle.y, doodle.width, doodle.height);
    prevDoodleY = doodle.y;
    // remove any platforms that have gone offscreen
    platforms = platforms.filter(function(platform) {
      return platform.y < canvas.height;
    })
  }
  // listen to keyboard events to move doodle
  document.addEventListener('keydown', function(e) {
    // left arrow key
    if (e.which === 37) {
      keydown = true;
      playerDir = -1;
      doodle.dx = -3;
    }
    // right arrow key
    else if (e.which === 39) {
      keydown = true;
      playerDir = 1;
      doodle.dx = 3;
    }
  });
  document.addEventListener('keyup', function(e) {
    keydown = false;
  });
  // start the game
  requestAnimationFrame(loop);
</script>
</body>
</html>