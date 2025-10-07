<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Surprise!</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: linear-gradient(135deg, #f6d365, #fda085);
      font-family: Arial, sans-serif;
      text-align: center;
    }
    button {
      padding: 15px 30px;
      font-size: 20px;
      border: none;
      border-radius: 10px;
      background-color: #4CAF50;
      color: white;
      cursor: pointer;
      transition: transform 0.2s;
    }
    button:hover {
      transform: scale(1.1);
    }
    #message {
      margin-top: 20px;
      font-size: 28px;
      font-weight: bold;
      color: #333;
      display: none;
    }
  </style>
</head>
<body>
  <div>
    <button onclick="showMessage()">Click Me!</button>
    <div id="message">Thank You, Mahomood! 💛</div>
  </div>

  <script>
    function showMessage() {
      document.getElementById('message').style.display = 'block';
    }
  </script>
</body>
</html>
