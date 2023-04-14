<html>
<head>
    <style>
    {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        }
        :root{
        --color-car-body:#24EA21;
        --color-bg-1:#e4ffff;
        }
        html{
        height: 100%;
        }
        body{
        background-image: linear-gradient(to top,#88d6e7 30%,#e4ffff 20%);
        overflow: hidden;
        }
        .car{
        position: absolute;
        top: 52.5%;
        left: 40%;
        /* transform: translate(-50%,-100%); */
        /* transform-origin: 25% bottom; */
        animation: start-car 8.5s 2.1s;
        z-index: 100;
        animation-iteration-count: 2;
        animation-direction: alternate;
        }
        /* .car__top{
        margin-left: 10vmin;
        width: 14vmin;
        height: 14vmin;
        transform: skew(-10deg);
        border:3vmin solid #4a4c48;
        border-radius: 1vmin;
        border-right: 0;
        } */
        /* .car__top::after{
        content: '';
        position: absolute;
        top: -3vmin;
        right: 0;
        width: 10vmin;
        height: 100%;
        transform:translateX(120%) skew(50deg);
        border:3vmin solid #4a4c48;
        border-left: 0;
        }
        .car__top::before{
        content: '';
        position: absolute;
        top: -.22vmin;
        right: 0;
        width: 16vmin;
        height: 100%;
        transform: translateX(70%) skew(10deg);
        border:3vmin solid #4a4c48;
        border-right: 0;
        border-top: 0;
        } */
        .car__body{
        width: 35vmin;
        height: 18vmin;
        background-color: var(--color-car-body);
        border-radius: 10vmin;
        margin-top: -1.5vmin;
        position: relative;
        z-index: 10;
        }
        .car__bulb{
        position: absolute;
        top: 14%;
        right: 2%;
        width: 2vmin;
        height: 4vmin;
        border-radius: 1rem / 1.4rem;
        transform: rotate(-40deg);
        background-color: #FFFFFF;
        }
        .car__bulb--back{
        top: 14%;
        left: 2%;
        transform: rotate(35deg);
        background-color:#FFFFFF;
        }
        .car__center{
        position: absolute;
        top: 50%;
        left:50%;
        transform: translate(-50%,-50%);
        width: 10vmin;
        height: 2vmin;
        border-radius: 2vmin;
        background-color: #fff;
        }
        .car__wheels{
        display: flex;
        justify-content: space-around;
        margin-top: -9vmin;
        position: relative;
        z-index: 200;
        }
        .car__wheel{
        --r:10vmin;
        width: var(--r);
        height:var(--r);
        border-radius: 50%;
        border: 1.8vmin solid #00A64C;
        background-color: #24EA21;
        position: relative;
        animation: run .5s 1s linear infinite;
        }
        .wheel__circle{
        --r:2.4vmin;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
        width:var(--r);
        height:var(--r);
        border-radius: 50%;
        background-color: #00A64C;
        }
        .wheel__rect{
        position: absolute;
        width: 2.8vmin;
        height: 3.1vmin;
        clip-path: polygon(0 0, 100% 0, 70% 100%, 30% 100%);
        background-color: #00A64C;
        }
        .wheel__rect--1{
        top: 30%;
        left: 35%;
        transform: translate(-50%,-50%) rotate(-40deg);
        }
        .wheel__rect--2{
        top: 30%;
        left: 64%;
        transform: translate(-50%,-50%) rotate(35deg);
        }
        .wheel__rect--3{
        top: 50%;
        left: 25%;
        transform: translate(-50%,-50%) rotate(-90deg);
        }
        .wheel__rect--4{
        top: 50%;
        left: 75%;
        transform: translate(-50%,-50%) rotate(90deg);
        }
        .wheel__rect--5{
        top: 70%;
        left: 35%;
        transform: translate(-50%,-50%) rotate(-145deg);
        }
        .wheel__rect--6{
        top: 70%;
        left: 64%;
        transform: translate(-50%,-50%) rotate(146deg);
        }
        #animate {
        width: 50px;
        height: 50px;
        position: absolute;
        background-color: green;
        }
        .cloud{
        position: absolute;
        top: var(--top);
        left: 0;
        width: 20vmin;
        height: 10vmin;
        border-radius: 10vmin 10vmin 0 6vmin;
        background-color: #b5edf9;
        -webkit-animation: cloud 5s var(--delay) linear infinite backwards;
        animation: cloud 5s var(--delay) linear infinite backwards;
        }
        .cloud::after {
        content: "";
        position: absolute;
        width: 20vmin;
        height: 12vmin;
        bottom: 0;
        border-radius: 6rem 10rem 1rem 0;
        -webkit-transform: translateX(9vmin);
        transform: translateX(9vmin);
        background-color: #b5edf9;
        }
        .cloud::before {
        content: "";
        position: absolute;
        width: 15vmin;
        height: 8vmin;
        bottom: 8vmin;
        border-radius: 20vmin 20vmin 0 0;
        -webkit-transform: translateX(6vmin);
        transform: translateX(6vmin);
        background-color: #b5edf9;
        }
        @keyframes cloud {
        0%{
        transform: translateX(100vw);
        }
        100%{
        transform: translateX(-100vw);
        }
        }
        @keyframes run {
        0%{
        transform: rotate(0deg);
        }
        100%{
        transform: rotate(360deg);
        }
        }
        @keyframes start-car {
        0%{
        transform: translate(0%, 0%);
        }
        5%{
            transform: translate(-30%, -175%);
        }
        10%{
            transform: translate(-50%, 0%);
        }
        15%{
        transform: translate(-80%,-175%);
        }
        20%{
        transform: translate(-100%,0%);
        }
        25%{
        transform: translate(-130%,-175%);
        }
        30%{
        transform: translate(-150%,0%);
        }
        35%{
        transform: translate(-120%,-175%);
        }
        40%{
        transform: translate(-100%, 0%);
        }
        45%{
        transform: translate(-70%,-175%);
        }
        50%{
        transform: translate(-50%,0%);
        }
        55%{
        transform: translate(-20%,-175%);
        }
        60%{
            transform: translate(0%, 0%);
        }
        65%{
            transform: translate(30%, -175%);
        }
        70%{
            transform: translate(50%, 0%);
        }
        75%{
            transform: translate(80%, -175%);
        }
        80%{
            transform: translate(100%, 0%);
        }
        85%{
            transform: translate(70%, -175%);
        }
        90%{
            transform: translate(50%, 0%);
        }
        95%{
            transform: translate(20%, -175%);
        }
        100%{
        transform: translate(0%,0%);
        }
        /* 5%{
        transform: translate(-40%,-100%);
        }
        15%{
        transform: translate(-45%,-100%);
        }
        25%{
        transform: translate(-45%,-100%) rotate(-20deg);
        }
        35%,45%,50%{
        transform: translate(-45%,-100%) rotate(0deg);
        }
        40%{
        transform: translate(-45%,-100%) rotate(-10deg);
        }
        47%{
        transform: translate(-45%,-100%) rotate(-5deg);
        }
        70%{
        transform: translate(20%,-100%) rotate(0deg);
        }
        100%{
        transform: translate(-50%,-100%) rotate(0deg);
        } */
        }
    </style>
</head>
<body>
    <div class="car">
        <div class="car__top"></div>
        <div class="car__body">
        <div class="car__bulb"></div>
        <div class="car__bulb car__bulb--back"></div>
        <div class="car__center"></div>
        </div>
        <div class="car__wheels">
        <div class="car__wheel car__wheel--1">
        <div class="wheel__circle"></div>
        <div class="wheel__rect wheel__rect--1"></div>
        <div class="wheel__rect wheel__rect--2"></div>
        <div class="wheel__rect wheel__rect--3"></div>
        <div class="wheel__rect wheel__rect--4"></div>
        <div class="wheel__rect wheel__rect--5"></div>
        <div class="wheel__rect wheel__rect--6"></div>
        </div>
        <div class="car__wheel car__wheel--2">
        <div class="wheel__circle"></div>
        <div class="wheel__rect wheel__rect--1"></div>
        <div class="wheel__rect wheel__rect--2"></div>
        <div class="wheel__rect wheel__rect--3"></div>
        <div class="wheel__rect wheel__rect--4"></div>
        <div class="wheel__rect wheel__rect--5"></div>
        <div class="wheel__rect wheel__rect--6"></div>
        </div>
        </div>
        </div>
        <div class="cloud" style="--delay:1s;--top:10vmin"></div>
        <div class="cloud" style="--delay:4s;--top:20vmin"></div>
        <div class="cloud" style="--delay:8s;--top:10vmin"></div>
</body>
</html>
<footer>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
</footer>