# codealpha_tasks
# new repo

<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Age Calculator</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&display=swap');

    body {
      font-family: 'Share Tech Mono', monospace;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-color: black;
      color: #0f0;
      overflow: hidden;
    }

    .container {
      text-align: center;
      background: rgba(0, 0, 0, 0.8);
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 0 15px #0f0;
      max-width: 400px;
    }

    h1 {
      font-size: 24px;
      color: #0f0;
      text-shadow: 0 0 10px #0f0;
    }

    label {
      display: block;
      margin: 10px 0 5px;
    }

    input {
      width: 100%;
      padding: 10px;
      margin-bottom: 15px;
      border: 1px solid #0f0;
      border-radius: 8px;
      background: black;
      color: #0f0;
      text-align: center;
    }

    button {
      background-color: black;
      color: #0f0;
      padding: 10px 20px;
      border: 1px solid #0f0;
      border-radius: 8px;
      cursor: pointer;
      font-size: 16px;
      text-shadow: 0 0 5px #0f0;
      transition: 0.3s ease;
    }

    button:hover {
      background-color: #0f0;
      color: black;
      box-shadow: 0 0 10px #0f0;
    }

    .result {
      margin-top: 20px;
      font-size: 18px;
      color: #0f0;
      text-shadow: 0 0 5px #0f0;  
      animation: blink 1s infinite alternate;
    }

    @keyframes blink {
      from {
        opacity: 1;
      }

      to {
        opacity: 0.7;
      }
    }
  </style>
</head>

<body>
  <div class="container">
    <h1>Age Calculator</h1>
    <form id="ageCalculatorForm">
      <label for="day">Day:</label>
      <input type="number" id="day" min="1" max="31" placeholder="Enter day" required>

      <label for="month">Month:</label>
      <input type="number" id="month" min="1" max="12" placeholder="Enter month" required>

      <label for="year">Year:</label>
      <input type="number" id="year" placeholder="Enter year" required>

      <button type="button" onclick="calculateAge()">Calculate</button>
      <button type="reset" onclick="resetForm()">Reset</button>
    </form>
    <div class="result" id="result"></div>
  </div>

  <script>
    function calculateAge() {
      const day = parseInt(document.getElementById('day').value);
      const month = parseInt(document.getElementById('month').value);
      const year = parseInt(document.getElementById('year').value);

      if (!day || !month || !year || day < 1 || day > 31 || month < 1 || month > 12) {
        document.getElementById('result').innerText = "Invalid input, Agent!";
        return;
      }

      const today = new Date();
      const birthDate = new Date(year, month - 1, day);

      if (birthDate > today) {
        document.getElementById('result').innerText = "Future detected! Try again.";
        return;
      }

      let age = today.getFullYear() - birthDate.getFullYear();
      const m = today.getMonth() - birthDate.getMonth();

      if (m < 0 || (m === 0 && today.getDate() < birthDate.getDate())) {
        age--;
      }

      document.getElementById('result').innerText = `Age: ${age} years`;
    }

    function resetForm() {
      document.getElementById('ageCalculatorForm').reset();
      document.getElementById('result').innerText = "";
    }
  </script>
</body>

</html>

