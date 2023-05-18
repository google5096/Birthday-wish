#Bithday
<!DOCTYPE html>
<html>
<head>
  <title>Happy Birthday!</title>
 
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
