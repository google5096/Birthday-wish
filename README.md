# Birthday-wish
<!DOCTYPE html>
<html>
<head>
  <title>Happy Birthday!</title>
  <style>
    *{
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
    body {
      font-family: Arial, sans-serif;
      background-color: #EAFDFC;
      text-align: center;
      padding-top: 100px;
    }
    span{
        color: rgb(92, 94, 92);
    }
    .header{
        width: 95vw;
        font-size: 3rem;
        margin-left: 3rem;
        margin-bottom: 2rem;
        color: rgb(40, 40, 92);
        background-color: rgb(126, 164, 131);
        opacity: 0.8;
        border-radius: 0.5rem;
    }
    .header:hover{
        letter-spacing: ;
    }
    h1 {
      color: #b30c4f;
      font-size: 40px;
      margin-bottom: 30px;
    }

    p:hover,h1:hover{
        transition: 2s;
        letter-spacing: 2px;
    }
    #bestie{
        font-size: 1.5rem;
      color: #b30c4f;

    }
    .container{
        margin-top: 0px;
        padding-right: 20%;

        display: flex;
        justify-content: center;
        align-items: center;
        padding-left: 19%;
        gap: 1rem;
    }
    .cake{
        display: flex;
        justify-content: center;
        align-items: center;
        margin-bottom: 1%;
        height: 100%;
        width: 100%;
    }

    .img{
        width: 20vw;
        border-radius: 5px;
    }
    .img-1{
        width: 26vw;
        border-radius: 50%;

    }

    .img-2{
        height: 60%;
        width: 30vw;
        border-radius: 10px;
    }

    .confetti {
      position: absolute;
      width: 10px;
      height: 10px;
      background-color: #ff0066;
      border-radius: 50%;
      opacity: 0.8;
      animation: confetti-fall linear infinite;
    }


    @keyframes vibrate {
  0% { transform: rotate(0deg); }
  10% { transform: rotate(-1deg); }
  20% { transform: rotate(1deg); }
  30% { transform: rotate(0deg); }
  40% { transform: rotate(1deg); }
  50% { transform: rotate(-1deg); }
  60% { transform: rotate(0deg); }
  70% { transform: rotate(-1deg); }
  80% { transform: rotate(1deg); }
  90% { transform: rotate(0deg); }
  100% { transform: rotate(-1deg); }
}

.img:hover,.img-1:hover,.img-2:hover {
  animation: vibrate 0.5s;


  animation-iteration-count: 2;
}

    @keyframes confetti-fall {
      0% {
        transform: translateY(-100vh) rotate(0deg);
      }
      100% {
        transform: translateY(100vh) rotate(360deg);
      }
    }
  </style>
</head>
<body>
    <div class="header"> <span>"</span> Friendship is a house that is built on and sustained by love. <span>"</span>  </div>

        <div class="cake"><img src="img/cake.jpg"  alt=""></div>

    <div class="container">
        <img class="img" src="img/Kartik.jpeg"  alt="">        
        <img class="img-1" src="img/h1.jpeg"  alt="">
        <img class="img-2" src="img/kartik-b.jpeg"  alt="">
    </div>
  <h1>Happy Birthday,<a href="https://www.google.com/search?q=hacker+img&tbm=isch&ved=2ahUKEwiAh5Lgpv3-AhWFqGMGHUTpAhkQ2-cCegQIABAA&oq=hacker&gs_lcp=CgNpbWcQARgAMgcIABCKBRBDMgoIABCKBRCxAxBDMgoIABCKBRCxAxBDMgoIABCKBRCxAxBDMgoIABCKBRCxAxBDMgoIABCKBRCxAxBDMgoIABCKBRCxAxBDMgoIABCKBRCxAxBDMgcIABCKBRBDMggIABCABBCxAzoECCMQJzoFCAAQgAQ6CwgAEIAEELEDEIMBUP4SWNUaYJMoaABwAHgAgAHmBIgBswuSAQcwLjYuNS0xmAEAoAEBqgELZ3dzLXdpei1pbWfAAQE&sclient=img&ei=4EdlZICXK4XRjuMPxNKLyAE&bih=533&biw=1266#imgrc=AOoa-DRBVXN6IM"> [Kartik:The Coder and ...]!</a></h1>
  <p>"Happy birthday to my incredible best friend<span id="bestie"> Kartik</span>! May your day be filled with love, laughter, and unforgettable moments."</p>
  <canvas id="confetti"></canvas>

  <script>
    function createConfetti() {
      const canvas = document.getElementById('confetti');
      const context = canvas.getContext('2d');

      const colors = ['#ff0066', '#00bfff', '#ffcc00', '#33cc33', '#ff33cc'];

      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;

      function randomInRange(min, max) {
        return Math.random() * (max - min) + min;
      }

      function Confetti() {
        this.x = randomInRange(0, canvas.width);
        this.y = randomInRange(-canvas.height, -10);
        this.rotation = randomInRange(0, 2 * Math.PI);
        this.color = colors[Math.floor(randomInRange(0, colors.length))];
        this.speed = randomInRange(2, 4);
        this.radius = randomInRange(5, 10);
      }

      Confetti.prototype.update = function() {
        this.y += this.speed;

        if (this.y > canvas.height) {
          this.y = randomInRange(-canvas.height, -10);
        }
      }

      Confetti.prototype.draw = function() {
        context.beginPath();
        context.save();
        context.translate(this.x, this.y);
        context.rotate(this.rotation);
        context.fillStyle = this.color;
        context.fillRect(-this.radius, -this.radius, 2 * this.radius, 2 * this.radius);
        context.restore();
        context.closePath();
      }

      const confettiCount = 100;
      const confetti = [];

      for (let i = 0; i < confettiCount; i++) {
        confetti.push(new Confetti());
      }

      function loop() {
        context.clearRect(0, 0, canvas.width, canvas.height);

        for (let i = 0; i < confetti.length; i++) {
          confetti[i].update();
          confetti[i].draw();
        }

        requestAnimationFrame(loop);
      }

      loop();
    }

    createConfetti();
  </script>
</body>
</html>


 46 changes: 46 additions & 0 deletions46  
Bithday1.html
@@ -0,0 +1,46 @@
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Birthday</title>
    <style>
        *{
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        .container{
            height: 100vh;
            width: 100vw;
            background-color: #EAFDFC;
        }

        .container-in{
            height: 100vh;
            width: 100vw;
            display: flex;
            justify-content: center;
            align-items: center;

        }
        button{
            padding: 0.6rem 2.3rem;
            text-align: center;
            font-size: 1.7rem;
            font-weight: 800px;
            color: rgb(47, 47, 202);

        }
    </style>
</head>
<body>
    <div class="container">
        <div class="container-in">
           <a href="Bithday.html"><button>Click ...👆</button></a> 
        </div>

    </div>
</body>
</html>
