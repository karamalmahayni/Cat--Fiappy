<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cat--Fiappy</title>

<style>
html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  font-family: Arial, sans-serif;
  background: #8fd3f4;
}

/* شاشة البداية */
#menu {
  position: fixed;
  inset: 0;
  background: #8fd3f4;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

/* عنوان اللعبة */
#title {
  font-size: 56px;
  font-weight: bold;
  color: #1e6cff;
  text-shadow: 4px 4px 8px rgba(0,0,0,0.4);
  margin-bottom: 40px;
}

/* زر البداية */
#startBtn {
  font-size: 22px;
  padding: 14px 36px;
  border: none;
  border-radius: 12px;
  cursor: pointer;
}

/* اللعبة */
canvas {
  display: none;
  background: #87ceeb;
}
</style>
</head>

<body>

<!-- شاشة البداية -->
<div id="menu">
  <div id="title">Cat--Fiappy</div>
  <button id="startBtn">ابدأ اللعبة</button>
</div>

<!-- اللعبة -->
<canvas id="game"></canvas>

<script>
const menu = document.getElementById("menu");
const startBtn = document.getElementById("startBtn");
const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let running = false;
let y = canvas.height / 2;
let vy = 0;
const gravity = 0.6;
const jump = -10;

startBtn.onclick = () => {
  menu.style.display = "none";
  canvas.style.display = "block";
  running = true;
};

canvas.addEventListener("click", () => {
  if (running) vy = jump;
});

function loop() {
  ctx.clearRect(0,0,canvas.width,canvas.height);

  if (running) {
    vy += gravity;
    y += vy;
  }

  // القطة (مؤقتًا دائرة)
  ctx.fillStyle = "#ffcc99";
  ctx.beginPath();
  ctx.arc(150, y, 22, 0, Math.PI * 2);
  ctx.fill();

  requestAnimationFrame(loop);
}

loop();
</script>

</body>
</html>
