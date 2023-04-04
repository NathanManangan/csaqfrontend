<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>

<body>
<div id='herocenterimage' class='herocenterimage'>
    <div id='background' class='background'>
    </div>
    <div id='browser' class='parent'>
      <img id='group' class='group' src="assets/css/images/browser.png" style="height: 100%; width: 100%; position:relative; left: 40%; top: 70%;" />
    </div>
    <div id='content' class='content'>
      <button id='buttonprimary' class='buttonprimary'>
        <div id='background3' class='background3'>
        </div>
        <div id='text' class='text'>
          Start</div>
      </button>
      <div id='subtitle' class='subtitle'>
        Learn how to ace your AP CSA test with our interactive features!</div>
      <div id='title2' class='title2'>
        Find All Your FRQs In One Place</div>
    </div>
  </div>
  <br>
  <br>
  <div style="background-color: #F2F2F2; position: relative; top:120%; margin-top: 5%">
  <br>
  <br>
    <a style="color:#011627; font-size:50px; margin-left: 34%; font-family: Ubuntu">Most Popular FRQs</a>
    <br>
    <br>
    <div class="row">
        <div class="column">
            <button class="columnbox"><img src="assets/css/images/frog.png" style="width:45%"></button>
        </div>
        <div class="column">
            <button class="columnbox"><img src="assets/css/images/game.png" style="width:70%"></button>
        </div>
        <div class="column">
            <button class="columnbox"><img src="assets/css/images/image.png" style="width:45%"></button>
        </div>
    </div>
  </div>

  <style>
    .row{
        height: 40%;
    }
    .columnbox{
        display: block;
        border-radius: 25px;
        background: #011627;
        padding: 20px; 
        width: 80%;
        margin-left: 10%;
        height: 80%;  
    }

    body::-webkit-scrollbar {
      display: none;
    }
    
    /* Hide scrollbar for IE, Edge and Firefox */
    .body {
      -ms-overflow-style: none;  /* IE and Edge */
      scrollbar-width: none;  /* Firefox */
    }
     
    /* first part of homepage css*/
    
    .herocenterimage {
      background-color:#ffffff;
      height:700px;
      width:1440px;
      padding:0px;
      border-style:hidden;
      outline:none;
      position:absolute;
    }
    
    .background {
      background-color:#274c77;
      height:700px;
      width:1440px;
    }
    
    #browser {
      width:800px;
      height:480px;
      left:0%;
      top: 0%;
      position:absolute;
      margin-top:5%;
    }
    
    .background2 {
      background-color:#d6daff;
      height:480px;
      width:800px;
      border-radius:36px;
      border:2px solid #000000;
      top:357px;
      left:320px;
      position:absolute;
    }

    .group {
      width:60px;
      height:12px;
      left:336px;
      top:373px;
      position:absolute;
    }
    .button {
      background-color:#ea7878;
      height:12px;
      width:12px;
      top:373px;
      left:336px;
      position:absolute;
      border-radius:50%;
    }

    .button2 {
      background-color:#e9f1bb;
      height:12px;
      width:12px;
      top:373px;
      left:360px;
      position:absolute;
      border-radius:50%;
    }

    .button3 {
      background-color:#a1d2ac;
      height:12px;
      width:12px;
      top:373px;
      left:384px;
      position:absolute;
      border-radius:50%;
    }
    
    .content {
      width:787px;
      height:224px;
      top:10%;
      left:20%;
      position:absolute;
    }
    
    .buttonprimary {
      background-color:#ffffff;
      height:60px;
      width:240px;
      padding:0px;
      border-style:hidden;
      outline:none;
      top: 212px;
      left:307px;
      position:absolute;
      text-align: center;
    }
    
    .background3 {
      background-color:#ffffff;
      height:60px;
      width:240px;
      filter:drop-shadow(0px 8px 4px rgba(0,0,0,0.25));
      border-radius:5px;
    }
    
    .text {
      color:#274c77;
      text-align:center;
      vertical-align:text-middle;
      font-size:18px;
      font-family:Ubuntu;
      left:25px;
      top:20px;
      width:191px;
      height:21px;
      position:absolute;
      line-height:auto;
      border-style:hidden;
      outline:none;
    }
    
    .subtitle {
      color:rgba(255, 255, 255, 0.5);
      text-align:center;
      vertical-align:text-middle;
      font-size:17px;
      font-family:Ubuntu;
      left:167px;
      top:73px;
      width:506px;
      height:51px;
      position:absolute;
      line-height:140.625px;
      border-style:hidden;
      outline:none;
    }
    
    .title2 {
      color:#ffffff;
      text-align:center;
      vertical-align:text-middle;
      font-size:48px;
      font-family:Ubuntu;
      left:36px;
      top:18px;
      width:787px;
      height:56px;
      position:absolute;
      line-height:auto;
      border-style:hidden;
      outline:none;
    }

    footer {
      style= position: relative;
      margin-top: 60%;
    }

    /* Social proof */

@import url("https://fonts.googleapis.com/css2?family=Ubuntu:wght@700&display=swap");

p {
  margin: 0;
}

.social-proof {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  width: 1440px;
  height: 379px;
  padding: 68px 109px 47px 139px;
  box-sizing: border-box;
  background-color: rgba(242, 242, 242, 1);
}
.group-086 {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  height: 100%;
  box-sizing: border-box;
}
.subtitle22 {
  display: flex;
  flex-direction: column;
  justify-content: center;
  color: rgba(39, 76, 119, 1);
  font-size: 40px;
  line-height: 141%;
  font-family: Ubuntu, sans-serif;
  font-weight: 700;
  text-align: center;
}

.group-454 {
  display: flex;
  flex-direction: row;
  width: 100%;
  box-sizing: border-box;
}
.logos {
  width: 751px;
  height: 100%;
}

.logos-1 {
  width: 316px;
  height: 100%;
}
    </style>

    