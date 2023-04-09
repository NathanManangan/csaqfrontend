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
    console.log("temp = " + temp);
    if (temp == 1) {
        document.getElementById('input4').innerHTML = "left";
    }
    else {
        document.getElementById('input4').innerHTML = "right";
    }
}

function moveFrog() {
      var frog = document.getElementById("frog");
      var distance = nextHopDistance;
      var direction = Math.random() >= 0.5 ? 'right' : 'left'; // randomly choose a direction
      frog.classList.add('move-' + direction); // add the appropriate CSS class based on the direction
      setTimeout(function() {
        frog.classList.remove('move-' + direction); // remove the CSS class after the animation completes
      }, 2000);
    }

</script>


<html>
<head>
  <style>
    #frog {
      width: 100px;
      height: 100px;
      position: relative;
      left:200px;
    }
    .move-right {
      animation-name: moveRight;
      animation-duration: 1s;
    }
    .move-left {
      animation-name: moveLeft;
      animation-duration: 1s;
    }
    @keyframes moveRight {
      from {left: 200;}
      to {left: 400px;}
    }
    @keyframes moveLeft {
      from {left: 200;}
      to {left: 0px;}
    }
  </style>
</head>
<body>
<img id="frog" src="assets/css/images/frogj.png" alt="frog">
  <br>
  <button onclick="moveFrog()">Move Frog</button>
    
  <script>
    
</script>
</body>
</html>
