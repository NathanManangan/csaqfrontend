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
        position: fixed;
        color: #000000;
        top: 0;
        left: 0;
        width: 300px;
        transform: translateX(6.25%);
      }
  </style>
</head>
<body>
  <div id="score">1</div>
<canvas width="375" height="667" id="game"></canvas>
<script>
    