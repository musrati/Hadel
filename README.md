<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Hearts Page</title>
<style>
  body {
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #ffe6f0;
    overflow: hidden;
    font-family: Arial, sans-serif;
  }

  #buttonContainer {
    position: absolute;
    top: 20px;
    text-align: center;
    width: 100%;
  }

  button {
    padding: 15px 30px;
    font-size: 18px;
    border: none;
    border-radius: 10px;
    background: #ff4d94;
    color: white;
    cursor: pointer;
    box-shadow: 0 5px 10px rgba(0,0,0,0.2);
  }

  .heart {
    position: absolute;
    font-size: 24px;
    color: red;
    animation: floatUp 5s linear infinite;
    pointer-events: none;
  }

  @keyframes floatUp {
    0% { transform: translateY(0) scale(1); opacity: 1; }
    100% { transform: translateY(-800px) scale(1.5); opacity: 0; }
  }
</style>
</head>
<body>

<div id="buttonContainer">
  <button onclick="addHearts()">Hadel</button>
</div>

<script>
function addHearts() {
  const numHearts = 10; // number of hearts per click
  for(let i=0; i<numHearts; i++){
    const heart = document.createElement('div');
    heart.classList.add('heart');
    heart.innerText = '❤️';
    
    // Random position
    heart.style.left = Math.random() * window.innerWidth + 'px';
    heart.style.top = Math.random() * window.innerHeight + 'px';
    
    document.body.appendChild(heart);

    // Remove heart after animation
    setTimeout(() => heart.remove(), 5000);
  }
}

// Add some hearts initially
addHearts();
</script>

</body>
</html>
