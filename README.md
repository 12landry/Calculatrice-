<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculatrice iOS Style</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: 'Helvetica Neue', sans-serif;
      background: #000;
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .calculator {
      width: 320px;
      background: #1c1c1c;
      border-radius: 30px;
      box-shadow: 0 0 20px rgba(255, 255, 255, 0.1);
      overflow: hidden;
    }

    .display {
      background: black;
      padding: 30px 20px;
      font-size: 48px;
      text-align: right;
      min-height: 80px;
      color: white;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 1px;
    }

    button {
      font-size: 24px;
      padding: 20px 0;
      border: none;
      outline: none;
      color: white;
      background: #333;
      transition: background 0.2s;
    }

    button:active {
      background: #444;
    }

    .operator {
      background: #ff9500;
    }

    .operator:active {
      background: #e08900;
    }

    .gray {
      background: #a5a5a5;
      color: black;
    }

    .zero {
      grid-column: span 2;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <div class="display" id="display">0</div>
    <div class="buttons">
      <button class="gray" onclick="clearDisplay()">AC</button>
      <button class="gray" onclick="toggleSign()">+/-</button>
      <button class="gray" onclick="percent()">%</button>
      <button class="operator" onclick="inputOperator('/')">÷</button>

      <button onclick="inputNumber('7')">7</button>
      <button onclick="inputNumber('8')">8</button>
      <button onclick="inputNumber('9')">9</button>
      <button class="operator" onclick="inputOperator('*')">×</button>

      <button onclick="inputNumber('4')">4</button>
      <button onclick="inputNumber('5')">5</button>
      <button onclick="inputNumber('6')">6</button>
      <button class="operator" onclick="inputOperator('-')">−</button>

      <button onclick="inputNumber('1')">1</button>
      <button onclick="inputNumber('2')">2</button>
      <button onclick="inputNumber('3')">3</button>
      <button class="operator" onclick="inputOperator('+')">+</button>

      <button class="zero" onclick="inputNumber('0')">0</button>
      <button onclick="inputNumber('.')">.</button>
      <button class="operator" onclick="calculate()">=</button>
    </div>
  </div>

  <script>
    let currentInput = '0';
    let operator = '';
    let previousInput = '';

    const display = document.getElementById('display');

    function updateDisplay() {
      display.textContent = currentInput;
    }

    function inputNumber(num) {
      if (currentInput === '0' && num !== '.') {
        currentInput = num;
      } else {
        currentInput += num;
      }
      updateDisplay();
    }

    function inputOperator(op) {
      if (currentInput === '') return;
      if (previousInput !== '') calculate();
      operator = op;
      previousInput = currentInput;
      currentInput = '';
    }

    function clearDisplay() {
      currentInput = '0';
      previousInput = '';
      operator = '';
      updateDisplay();
    }

    function toggleSign() {
      currentInput = (parseFloat(currentInput) * -1).toString();
      updateDisplay();
    }

    function percent() {
      currentInput = (parseFloat(currentInput) / 100).toString();
      updateDisplay();
    }

    function calculate() {
      if (previousInput === '' || currentInput === '') return;
      const prev = parseFloat(previousInput);
      const curr = parseFloat(currentInput);
      let result = 0;

      switch (operator) {
        case '+': result = prev + curr; break;
        case '-': result = prev - curr; break;
        case '*': result = prev * curr; break;
        case '/': result = prev / curr; break;
      }

      currentInput = result.toString();
      operator = '';
      previousInput = '';
      updateDisplay();
    }
  </script>
</body>
</html>
