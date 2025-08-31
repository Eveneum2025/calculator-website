[index.html](https://github.com/user-attachments/files/22068310/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Smart Calculator</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: linear-gradient(135deg, #6a11cb, #2575fc);
      font-family: Arial, sans-serif;
      margin: 0;
    }
    .calculator {
      background: #fff;
      padding: 20px;
      border-radius: 20px;
      box-shadow: 0px 10px 25px rgba(0, 0, 0, 0.2);
      width: 320px;
    }
    .calculator input {
      width: 100%;
      height: 60px;
      margin-bottom: 20px;
      font-size: 24px;
      text-align: right;
      border: none;
      border-radius: 10px;
      background: #f3f3f3;
      padding-right: 10px;
    }
    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }
    button {
      height: 60px;
      font-size: 20px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      background: #f1f1f1;
      transition: 0.2s;
    }
    button:hover { background: #ddd; }
    .operator { background: #2575fc; color: white; }
    .equal { background: #6a11cb; color: white; grid-column: span 2; }
    .clear { background: #ff4d4d; color: white; grid-column: span 2; }
  </style>
</head>
<body>
  <div class="calculator">
    <input type="text" id="display" disabled />
    <div class="buttons">
      <button onclick="clearDisplay()" class="clear">C</button>
      <button onclick="appendValue('/')">÷</button>
      <button onclick="appendValue('*')">×</button>
      <button onclick="appendValue('-')">−</button>

      <button onclick="appendValue('7')">7</button>
      <button onclick="appendValue('8')">8</button>
      <button onclick="appendValue('9')">9</button>
      <button onclick="appendValue('+')" class="operator">+</button>

      <button onclick="appendValue('4')">4</button>
      <button onclick="appendValue('5')">5</button>
      <button onclick="appendValue('6')">6</button>
      <button onclick="appendValue('.')">.</button>

      <button onclick="appendValue('1')">1</button>
      <button onclick="appendValue('2')">2</button>
      <button onclick="appendValue('3')">3</button>
      <button onclick="calculate()" class="equal">=</button>

      <button onclick="appendValue('0')" style="grid-column: span 4;">0</button>
    </div>
  </div>

  <script>
    const display = document.getElementById("display");
    function appendValue(value) { display.value += value; }
    function clearDisplay() { display.value = ""; }
    function calculate() {
      try { display.value = eval(display.value); }
      catch { display.value = "Error"; }
    }
    // Basic keyboard support
    document.addEventListener('keydown', (e) => {
      const allowed = '0123456789+-*/.';
      if (allowed.includes(e.key)) appendValue(e.key);
      if (e.key === 'Enter') calculate();
      if (e.key === 'Backspace') display.value = display.value.slice(0, -1);
      if (e.key.toLowerCase() === 'c' && (e.ctrlKey || e.metaKey)) clearDisplay();
    });
  </script>
</body>
</html>
