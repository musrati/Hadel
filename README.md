<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>أحبك يا هديلي ❤️</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      background: radial-gradient(circle at top left, #ff99cc, #660033);
      overflow: hidden;
      font-family: 'Cairo', sans-serif;
    }

    .heart {
      font-size: 100px;
      cursor: pointer;
      animation: pump 0.8s infinite alternate;
      transition: transform 1.2s ease, opacity 1.2s ease;
    }

    @keyframes pump {
      from { transform: scale(1); }
      to { transform: scale(1.25); }
    }

    .float {
      animation: floatUp 1.2s ease forwards;
    }

    @keyframes floatUp {
      0% { transform: translateY(0) scale(1); opacity: 1; }
      100% { transform: translateY(-180px) scale(1.4); opacity: 0; }
    }

    .text {
      color: white;
      font-size: 2.3rem;
      text-shadow: 0 0 15px #ff99cc, 0 0 30px #ff66b2, 0 0 45px #ff3399;
      opacity: 0;
      transform: translateY(30px);
      transition: all 0.9s ease-in-out;
    }

    .text.show {
      opacity: 1;
      transform: translateY(0);
    }
  </style>
</head>
<body>
  <div class="heart" id="heart">❤️</div>
  <div class="text" id="text">هديلي.. أجمل فتاة في العالم 💖</div>

  <script>
    const heart = document.getElementById('heart');
    const text = document.getElementById('text');

    heart.addEventListener('click', () => {
      heart.classList.add('float');
      heart.style.animation = 'none'; // توقف نبض القلب
      setTimeout(() => {
        heart.style.display = 'none';
        text.classList.add('show');
      }, 1000); // بعد ثانية واحدة فقط
    });
  </script>
</body>
</html>
