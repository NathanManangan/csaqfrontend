<!-- button to start -->
<div lik style="margin: 0 auto; text-align: center">
<input type="text" id="distanceGoal" name="distanceGoal" placeholder="Enter desired distance here (integer, max 30)"
    style="width: 50%;
  padding: 5px 5px;
  margin: 8px 0;
  box-sizing: border-box
  border: 2px solid #000000;
  border-radius: 40px;
  color: black;">
  <input type="text" id="maxHops" name="maxHops" placeholder="Enter maximum Hops (integer, max 6)"
    style="width: 50%;
  padding: 5px 5px;
  margin: 8px 0;
  box-sizing: border-box;
  border: 2px solid #000000;
  border-radius: 40px;
  color: black;">
    <button type="submit" onclick="startSimulation()">Begin Simulation</button>
</div>

<!-- button to generate jump distance -->
<div lik style="margin: 0 auto; text-align: center">
    <button type="submit" onclick="jumpDistance()">Get Next Jump Distance</button>
</div>

<!-- button to generate positive or negative -->
<div lik style="margin: 0 auto; text-align: center">
    <button type="submit" onclick="jumpSign()">Get Next Jump Sign</button>
</div>

<body>

<ul style="color: white">
  <li>Distance Goal: <p id="input1"></p> </li>
  <li>Maximum hops allowed: <p id="input2"></p> </li>
  <li>Next Hop Distance: <p id="input3"></p> </li>
  <li>Next Hop Direction: <p id="input4"></p> </li>
</ul>
</body>

<script type="text/javascript">

var nextHopDistance = 0;

function startSimulation() {
    
    var distanceGoal = document.getElementById('distanceGoal').value;
    var maxHops = document.getElementById('maxHops').value;
    var nextHopDirection = '';
    var hmm = '--FourHundred';

    if (Math.round(distanceGoal) % 1 == 0 && Math.round(maxHops) % 1 == 0) {

        if (Math.round(distanceGoal) <= 30 && Math.round(maxHops) <= 6) {
            document.getElementById('input1').innerHTML = Math.round(distanceGoal);
            document.getElementById('input2').innerHTML = Math.round(maxHops);
        }
        else if (Math.round(distanceGoal) > 30){
            alert("Distance cannot be greater than 30");
        }
        else {
            alert("Max Hops cannot be greater than 6");
        }
        
    }
    else {
        console.log("nonono");
        alert("Please make sure you inputted integers");
    }
}

function jumpDistance() {
    nextHopDistance = Math.floor(Math.random() * 6 + 1);
    document.getElementById('input3').innerHTML = nextHopDistance;
    console.log(nextHopDistance);
}

function jumpSign() {
    var temp = Math.floor(Math.random() * 3 + 1)
    nextHopDirection = '';
    if (temp == 1) {
        document.getElementById('input4').innerHTML = 'left';
        nextHopDirection = 'left'
    }
    else {
        document.getElementById('input4').innerHTML = 'right';
        nextHopDirection = 'right';

    }
}

function moveFrog() {
      var frog = document.getElementById("frog");
      var distance = nextHopDistance;
      var direction = nextHopDirection; // matches direction with that of button 
      frog.classList.add('move-' + direction + nextHopDistance); // add the appropriate CSS class based on the direction
      setTimeout(function() {
        frog.classList.remove('move-' + direction + nextHopDistance); // remove the CSS class after the animation completes
      }, 2000);
    }

</script>


<html>
<head>
  <style>
    :root {
    --FourHundred: 400px
    }
    #frog {
      width: 100px;
      height: 100px;
      position: relative;
      left:200px;
    }
    .move-right1 {
      animation-name: moveRight1;
      animation-duration: 2s;
    }
    .move-left1 {
      animation-name: moveLeft1;
      animation-duration: 2s;
    }
    .move-right2 {
      animation-name: moveRight2;
      animation-duration: 2s;
    }
    .move-left2 {
      animation-name: moveLeft2;
      animation-duration: 2s;
    }
    .move-right3 {
      animation-name: moveRight3;
      animation-duration: 2s;
    }
    .move-left3 {
      animation-name: moveLeft3;
      animation-duration: 2s;
    }
    .move-right4 {
      animation-name: moveRight4;
      animation-duration: 2s;
    }
    .move-left4 {
      animation-name: moveLeft4;
      animation-duration: 2s;
    }
    .move-right5 {
      animation-name: moveRight5;
      animation-duration: 2s;
    }
    .move-left5 {
      animation-name: moveLeft5;
      animation-duration: 2s;
    }
    .move-right6 {
      animation-name: moveRight6;
      animation-duration: 2s;
    }
    .move-left6 {
      animation-name: moveLeft6;
      animation-duration: 2s;
    }
    @keyframes moveRight1 {
      from {left: 200;}
      to {left: 250;}
    }
    @keyframes moveLeft1 {
      from {left: 200;}
      to {left: 150px;}
    }
    @keyframes moveRight2 {
      from {left: 200;}
      to {left: 300;}
    }
    @keyframes moveLeft2 {
      from {left: 200;}
      to {left: 100px;}
    }
    @keyframes moveRight3 {
      from {left: 200;}
      to {left: 350;}
    }
    @keyframes moveLeft3 {
      from {left: 200;}
      to {left: 50px;}
    }
    @keyframes moveRight4 {
      from {left: 200;}
      to {left: 400;}
    }
    @keyframes moveLeft4 {
      from {left: 200;}
      to {left: 0px;}
    }
    @keyframes moveRight5 {
      from {left: 200;}
      to {left: 450;}
    }
    @keyframes moveLeft5 {
      from {left: 200;}
      to {left: -50px;}
    }
    @keyframes moveRight6 {
      from {left: 200;}
      to {left: 500;}
    }
    @keyframes moveLeft6 {
      from {left: 200;}
      to {left: -100px;}
    }
  </style>
</head>

<body>
<!-- button to move frog -->
<div lik style="margin: 0 auto; text-align: center">
    <button type="submit" onclick="moveFrog()">Move Frog</button>
</div>
<img id="frog" src="frogj.png" alt="frog">
  <br>

    
  <script>
    
</script>
</body>
</html>
