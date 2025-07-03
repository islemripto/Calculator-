<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>آلة حاسبة</title>
  <style>
    body {
      background: #1e1e2f;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .calculator {
      background: #2e2e3e;
      padding: 20px;
      border-radius: 20px;
      box-shadow: 0 15px 25px rgba(0,0,0,0.3);
    }

    #display {
      width: 100%;
      height: 50px;
      font-size: 1.5em;
      margin-bottom: 10px;
      text-align: right;
      padding: 10px;
      border: none;
      border-radius: 10px;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 60px);
      gap: 10px;
    }

    button {
      padding: 15px;
      font-size: 1.2em;
      border: none;
      border-radius: 10px;
      background-color: #444;
      color: white;
      cursor: pointer;
      transition: background 0.3s ease;
    }

    button:hover {
      background-color: #555;
    }

    .zero {
      grid-column: span 2;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <input type="text" id="display" disabled />
    <div class="buttons">
      <button onclick="clearDisplay()">C</button>
      <button onclick="deleteLast()">←</button>
      <button onclick="appendToDisplay('/')">÷</button>
      <button onclick="appendToDisplay('*')">×</button>

      <button onclick="appendToDisplay('7')">7</button>
      <button onclick="appendToDisplay('8')">8</button>
      <button onclick="appendToDisplay('9')">9</button>
      <button onclick="appendToDisplay('-')">−</button>

      <button onclick="appendToDisplay('4')">4</button>
      <button onclick="appendToDisplay('5')">5</button>
      <button onclick="appendToDisplay('6')">6</button>
      <button onclick="appendToDisplay('+')">+</button>

      <button onclick="appendToDisplay('1')">1</button>
      <button onclick="appendToDisplay('2')">2</button>
      <button onclick="appendToDisplay('3')">3</button>
      <button onclick="calculateResult()">=</button>

      <button onclick="appendToDisplay('0')" class="zero">0</button>
      <button onclick="appendToDisplay('.')">.</button>
    </div>
  </div>

  <script>
    function appendToDisplay(value) {
      document.getElementById('display').value += value;
    }

    function clearDisplay() {
      document.getElementById('display').value = '';
    }

    function deleteLast() {
      const display = document.getElementById('display');
      display.value = display.value.slice(0, -1);
    }

    function calculateResult() {
      try {
        const result = eval(document.getElementById('display').value);
        document.getElementById('display').value = result;
      } catch {
        document.getElementById('display').value = 'خطأ';
      }
    }
  </script>
</body>
</html>
