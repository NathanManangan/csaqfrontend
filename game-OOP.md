<html>
<head>
  <title>Basic Doodle Jump HTML Game</title>
  <meta charset="UTF-8">
  <style>
      html, body {
        height: 100%;  
        margin: 0;
      }  
      body {
        text-align: center;
        align-items: center; 
      }
      canvas {
        border: 2px solid #FF0000;
        background-color: #E6E6E6;
        border-radius: 10px;
        box-shadow: 0px 0px 10px #FF0000;
        display: block;
        margin: 0;
        height: 100%;
      }
      #score {
        font-size: 2em;
        font-weight: bold;
        position: absolute;
        top: 1;
        left: 52%;
        transform: translateX(-50%);
      }
  </style>
</head>
<body>
  <div id="score">1</div>
<canvas width="375" height="667" id="game"></canvas>
<script>
class DoodleJumper {
  constructor() {
        //initializing the canvas 
        this.canvas = document.getElementById('game');
        this.context = this.canvas.getContext('2d');
        // width and height of each platform and where platforms start
        this.platformWidth = 65;
        this.platformHeight = 20;
        this.platformStart = this.canvas.height - 50;
        // player physics
        this.gravity = 0.33;
        this.drag = 0.3;
        this.bounceVelocity = -12.5;
        // minimum and maximum vertical space between each platform
        this.minPlatformSpace = 15;
        this.maxPlatformSpace = 20;
        // variable to keep track of score
        this.score = 0;
        // the doodle jumper
        this.doodle = {
            width: 40,
            height: 60,
            x: this.canvas.width / 2 - 20,
            y: this.platformStart - 60,
            dx: 0,
            dy: 0
        };
        // keep track of player direction and actions
        this.playerDir = 0;
        this.keydown = false;
        this.prevDoodleY = this.doodle.y;
        // bind event listeners
        this.handleKeyDown = this.handleKeyDown.bind(this);
        this.handleKeyUp = this.handleKeyUp.bind(this);
        document.addEventListener('keydown', this.handleKeyDown);
        document.addEventListener('keyup', this.handleKeyUp);
        // fill the initial screen with platforms
        this.platforms = [{
            x: this.canvas.width / 2 - this.platformWidth / 2,
            y: this.platformStart
        }];
        this.generatePlatforms();
    }
    //method to generate platforms randomly using min and max 
  generatePlatforms() {
    let y = this.platformStart;
    while (y > 0) {
        // the next platform can be placed above the previous one with a space
        // somewhere between the min and max space
        //calling the helper method random 
        y -= this.platformHeight + this.random(this.minPlatformSpace, this.maxPlatformSpace);
        // a platform can be placed anywhere 25px from the left edge of the canvas
        // and 25px from the right edge of the canvas (taking into account platform
        // width).
        // however the first few platforms cannot be placed in the center so
        // that the player will bounce up and down without going up the screen
        // until they are ready to move
        let x;
        do {
            x = this.random(25, this.canvas.width - 25 - this.platformWidth);
        } while (
            y > this.canvas.height / 2 &&
            x > this.canvas.width / 2 - this.platformWidth * 1.5 &&
            x < this.canvas.width / 2 + this.platformWidth / 2
        );
        this.platforms.push({ x, y });
    }
  }
  // helper method to generate platforms
    random(min, max) {
        //inclusive of min, but exclusive of max
        return Math.random() * (max - min) + min;
    }
    ///////////////////////// Start of Controller methods ///////////////////////////
    //
  handleKeyDown(e) {
    //left arrow key
    if (e.which === 37) {
      this.keydown = true;
      this.playerDir = -1;
      this.doodle.dx = -3;
    } else if (e.which === 39) {
      this.keydown = true;
      this.playerDir = 1;
      this.doodle.dx = 3;
    }
  }
  handleKeyUp() {
    this.keydown = false;
  }
  updateScore() {
    this.score++;
  }
  //game start for the loop 
  loop() {
    //repeating the loop
    requestAnimationFrame(() => this.loop());
    this.context.clearRect(0, 0, this.canvas.width, this.canvas.height);
    // apply gravity to doodle
    this.doodle.dy += this.gravity;
    // if doodle reaches the middle of the screen, move the platforms down
    // instead of doodle up to make it look like doodle is going up
    if (this.doodle.y < this.canvas.height / 2 && this.doodle.dy < 0) {
      this.platforms.forEach((platform) => {
        platform.y += -this.doodle.dy;
      });
      // add more platforms to the top of the screen as doodle moves up
      while (this.platforms[this.platforms.length - 1].y > 0) {
        this.platforms.push({
          x: this.random(25, canvas.width - 25 - platformWidth),
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
  //updateScore();
  DoodleJumper.loop();
</script>
</body>


<body>
<p>Hashmap array</p>

<p id="demo"></p>

<script>
// Create a Map
const scores = new Map([
  ["jim", 500],
  ["knish", 300],
  ["monkey", 200]
]);

document.getElementById("demo").innerHTML = scores.get("knish");
</script>

</body>
</html>