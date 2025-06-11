<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Advanced Calculator</title>
  <style>
    * {
      box-sizing: border-box;
      font-family: 'Segoe UI', sans-serif;
    }

    body {
      margin: 0;
      height: 100vh;
      background: linear-gradient(270deg, #ff6ec4, #7873f5, #3cf6c2, #ffc93c);
      background-size: 800% 800%;
      animation: gradientBG 12s ease infinite;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    @keyframes gradientBG {
      0% {background-position: 0% 50%;}
      50% {background-position: 100% 50%;}
      100% {background-position: 0% 50%;}
    }

    .calculator {
      background-color: rgba(255, 255, 255, 0.95);
      padding: 25px;
      border-radius: 20px;
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
      width: 300px;
    }

    .display {
      background-color: #e3e3e3;
      padding: 15px;
      border-radius: 10px;
      margin-bottom: 15px;
      font-size: 1.8rem;
      text-align: right;
      word-wrap: break-word;
      min-height: 50px;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 12px;
    }

    button {
      padding: 18px;
      font-size: 1.1rem;
      border: none;
      border-radius: 10px;
      background: #6c63ff;
      color: white;
      cursor: pointer;
      transition: 0.3s ease;
    }

    button:hover {
      background: #5548e0;
    }

    button.operator {
      background-color: #ffa500;
    }

    button.operator:hover {
      background-color: #cc8400;
    }

    .made-by {
      margin-top: 15px;
      text-align: center;
      font-weight: bold;
      color: #333;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <div class="display" id="display">0</div>
    <div class="buttons">
      <button onclick="clearDisplay()">C</button>
      <button onclick="append('%')">%</button>
      <button onclick="append('/')">/</button>
      <button onclick="backspace()">⌫</button>

      <button onclick="append('7')">7</button>
      <button onclick="append('8')">8</button>
      <button onclick="append('9')">9</button>
      <button onclick="append('*')" class="operator">*</button>

      <button onclick="append('4')">4</button>
      <button onclick="append('5')">5</button>
      <button onclick="append('6')">6</button>
      <button onclick="append('-')" class="operator">-</button>

      <button onclick="append('1')">1</button>
      <button onclick="append('2')">2</button>
      <button onclick="append('3')">3</button>
      <button onclick="append('+')" class="operator">+</button>

      <button onclick="append('0')">0</button>
      <button onclick="append('.')">.</button>
      <button onclick="calculate()" style="grid-column: span 2; background-color: #28a745;">=</button>
    </div>
    <div class="made-by">Made by Shubham</div>
  </div>

  <script>
    const display = document.getElementById('display');

    function append(value) {
      if (display.innerText === "0" || display.innerText === "Error") {
        display.innerText = value;
      } else {
        display.innerText += value;
      }
    }

    function clearDisplay() {
      display.innerText = "0";
    }

    function backspace() {
      let current = display.innerText;
      display.innerText = current.length > 1 ? current.slice(0, -1) : "0";
    }

    function calculate() {
      try {
        display.innerText = eval(display.innerText.replace('%', '/100'));
      } catch (e) {
        display.innerText = "Error";
      }
    }
  </script>
</body>
</html>
