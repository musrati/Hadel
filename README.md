<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>I Love You Hadell ❤️</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: radial-gradient(circle at top left, #ff99cc, #660033);
      overflow: hidden;
      font-family: 'Poppins', sans-serif;
    }

    h1 {
      color: white;
      font-size: 3rem;
      text-shadow: 0 0 20px #ff99cc, 0 0 40px #ff66b2, 0 0 60px #ff3399;
      animation: glow 2s infinite alternate;
    }

    @keyframes glow {
      from { text-shadow: 0 0 10px #ff99cc, 0 0 20px #ff66b2; }
      to { text-shadow: 0 0 30px #ff66b2, 0 0 60px #ff3399; }
    }

    .heart {
      position: absolute;
      color: #ff99cc;
      font-size: 20px;
      animation: floatUp 5s linear infinite;
      opacity: 0.8;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(0) scale(1);
        opacity: 1;
      }
      100% {
        transform: translateY(-800px) scale(1.5);
        opacity: 0;
      }
    }
  </style>
</head>
<body>
  <h1>I Love You, Hadell ❤️</h1>

  <script>
    // Create floating hearts
    function createHeart() {
      const heart = document.createElement('div');
      heart.classList.add('heart');
      heart.textContent = '❤️';
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.fontSize = Math.random() * 20 + 20 + 'px';
      document.body.appendChild(heart);

      setTimeout(() => {
        heart.remove();
      }, 5000);
    }

    setInterval(createHeart, 300);
  </script>
</body>
</html>
