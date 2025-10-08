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
      flex-direction: column;
    }

    .heart {
      font-size: 100px;
      cursor: pointer;
      animation: pump 1s infinite alternate;
      transition: transform 2s ease, opacity 2s ease;
    }

    @keyframes pump {
      from { transform: scale(1); }
      to { transform: scale(1.2); }
    }

    .float {
      animation: floatUp 2.5s ease forwards;
    }

    @keyframes floatUp {
      0% { transform: translateY(0) scale(1); opacity: 1; }
      100% { transform: translateY(-200px) scale(1.5); opacity: 0; }
    }

    .text {
      color: white;
      font-size: 2rem;
      text-shadow: 0 0 20px #ff99cc, 0 0 40px #ff66b2, 0 0 60px #ff3399;
      opacity: 0;
      transform: translateY(40px);
      transition: all 1.5s ease;
    }

    .text.show {
      opacity: 1;
      transform: translateY(0);
    }
  </style>
</head>
<body>
  <div class="heart" id="heart">❤️</div>
  <div class="text" id="text">Hadel, the prettiest girl in the world 💖</div>

  <script>
    const heart = document.getElementById('heart');
    const text = document.getElementById('text');

    heart.addEventListener('click', () => {
      heart.classList.add('float');
      heart.style.animation = 'none'; // stop pumping
      setTimeout(() => {
        heart.style.display = 'none';
        text.classList.add('show');
      }, 2000);
    });
  </script>
</body>
</html>

