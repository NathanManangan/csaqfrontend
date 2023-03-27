<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<div id='herocenterimage' class='herocenterimage'>
    <div id='background' class='background'>
    </div>
    <div id='browser' class='parent'>
      <div id='background2' class='background2'></div>
      <img id='group' class='group'
        src='data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAMCAYAAAA+ht7fAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAJDSURBVHgB5ZZPSBRhGMaf7KDUxgxoq2y0bohLhy2KoIuHwryEe4rAoMuIBC0UXSoiWkrYoD9eWgilg3bxIBR4WJYOuq2QENFSCFkuyIbS0paHxj+Lnup9v9nPRne/wzgLCj7wLO98+34/eOYdvhngv3TyffJb8t+SP5ENVEc7ih8g52yNm50r9WxVgZ3C31PaIBYOaxrinZ0INTVBq61FcmYG0fFxzJsm93wnnyT/gXNZfH8j4v23EDrWAk33IJmYRPROP+bnClXhN/gO4krsGpqPBrDvwH5kUh8w/HgIC/nf63wObJCHOGyqp0cEtctcXUX74KAM3Ut+AGcyBJ/Cpt4NiKAb+OYy2tuuytBb5nPY2Ks+EdSu4tIK7l28KUP31tDPDa5iHR1lYVlaXR3i4bC8PAPnsviPImVhBV/ziKm75V++3V0WlsVrPHXJ58AnuDofDCqJIa9XlmfhXBY/3KbmH29xzT917rSygR9xya+Rlbm2ptzAU3YrfnSVfM0DtyouFZX/2SfPgdNcfCkUlBuS2awsP8O50oI/Navm0+Hllj/3Lads4MNL8jnwBFfXE4mKU16ktejYmLx8Buey+JG+ilNeNFfopB5wzX8RfV5xyrw2/OTlOn8vrLt6iYLpo9PT8Os6WuvrRdBMPo+ukRH7a6kbzmXxzWV99PUE/M2NaA36RdDMx6/ounCXTuifrvl0Guvv30yiweeF78ghEXR2KounkYdY+PGrjB/ALvnw2CwD1h2TjWlY70Ud1ZGx3fx/c6AOun+CSDYAAAAASUVORK5CYII=' />
      <img id ='group' class="group" src="assets/css/images/home-browser.png" alt="HTML5 Icon" style="width:450px;height:298px; position:relative; left: 52%; top: 90%;"/>
    </div>f
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

  <style>
    body::-webkit-scrollbar {
        display: none;
    }
    
    /* Hide scrollbar for IE, Edge and Firefox */
    .body {
      -ms-overflow-style: none;  /* IE and Edge */
      scrollbar-width: none;  /* Firefox */
    }
    
    
    /* first part of homepage css*/
    
      .herocenterimage
    {
    background-color:#ffffff;
    height:700px;
    width:1440px;
    padding:0px;
    border-style:hidden;
    outline:none;
    position:absolute;
    }
    .background
    {
    background-color:#274c77;
    height:700px;
    width:1440px;
    }
    #browser
    {
    width:800px;
    height:480px;
    left:0%;
    top: 0%;
    position:absolute;

    margin-top:5%;
    }
    .background2
    {
    background-color:#d6daff;
    height:480px;
    width:800px;
    border-radius:36px;
    border:2px solid #000000;
    top:357px;
    left:320px;
    position:absolute;
    }
    .group
    {
    width:60px;
    height:12px;
    left:336px;
    top:373px;
    position:absolute;
    }
    .button
    {
    background-color:#ea7878;
    height:12px;
    width:12px;
    top:373px;
    left:336px;
    position:absolute;
    border-radius:50%;
    }
    .button2
    {
    background-color:#e9f1bb;
    height:12px;
    width:12px;
    top:373px;
    left:360px;
    position:absolute;
    border-radius:50%;
    }
    .button3
    {
    background-color:#a1d2ac;
    height:12px;
    width:12px;
    top:373px;
    left:384px;
    position:absolute;
    border-radius:50%;
    }
    .content
    {
    width:787px;
    height:224px;
    top:10%;
    left:20%;
    position:absolute;
    }
    .buttonprimary
    {
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
    .background3
    {
    background-color:#ffffff;
    height:60px;
    width:240px;
    filter:drop-shadow(0px 8px 4px rgba(0,0,0,0.25));
    border-radius:5px;
    }
    .text
    {
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
    .subtitle
    {
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
    .title2
    {
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
    footer{
      style= position: relative;
      margin-top: 60%;
    }
    </style>