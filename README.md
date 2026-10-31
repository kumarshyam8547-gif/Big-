OUT</button>

  <h3>वर्चुअल पॉइंट्स: <span id="score">1000</span></h3>

</div>

<script><!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Aviator Demo Game</title>

<style>
body {
  margin: 0;
  background: #101820;
  color: white;
  font-family: Arial, sans-serif;
  text-align: center;
}

h1 {
  color: #ff4242;
}

.game {
  margin: 20px;
  padding: 20px;
  background: #202d38;
  border-radius: 15px;
}

#plane {
  font-size: 55px;
  margin: 30px;
}

#multiplier {
  font-size: 40px;
  color: #00ff99;
}

button {
  padding: 14px 25px;
  margin: 8px;
  border: none;
  border-radius: 10px;
  font-size: 18px;
  background: #ff4242;
  color: white;
}

#message {
  font-size: 20px;
  margin: 15px;
}
</style>
</head>

<body>

<h1>✈ AVIATOR DEMO</h1>

<div class="game">

  <div id="plane">✈️</div>

  <div id="multiplier">1.00x</div>

  <div id="message">गेम शुरू करने के लिए दबाएं</div>

  <button onclick="startGame()">START</button>

  <button onclick="cashOut()">CASH 
let multiplier = 1;
let score = 1000;
let running = false;
let timer;
let crashAt = 0;

function startGame() {

  if (running) return;

  multiplier = 1;
  crashAt = 2 + Math.random() * 8;
  running = true;

  document.getElementById("message").innerText =
    "हवाई जहाज उड़ रहा है!";

  document.getElementById("plane").style.transform =
    "translateY(-20px)";

  timer = setInterval(() => {

    multiplier += 0.05;

    document.getElementById("multiplier").innerText =
      multiplier.toFixed(2) + "x";

    if (multiplier >= crashAt) {

      clearInterval(timer);
      running = false;

      document.getElementById("message").innerText =
        "CRASH! ✈️ गेम खत्म";

      document.getElementById("plane").style.transform =
        "translateY(0px)";
    }

  }, 150);
}

function cashOut() {

  if (!running) return;

  clearInterval(timer);
  running = false;

  let points = Math.floor(multiplier * 10);

  score += points;

  document.getElementById("score").innerText = score;

  document.getElementById("message").innerText =
    "आपने " + points + " वर्चुअल पॉइंट्स जीते!";
}
</script>

</body>
</html>
