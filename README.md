<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Lease Renewal Cost Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f1f1f1;
      padding: 20px;
    }

    .lease-calc-container {
      max-width: 420px;
      margin: auto;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    .lease-calc-container h3 {
      text-align: center;
      margin-bottom: 20px;
      color: #046172;
    }

    .lease-calc-container label {
      font-weight: bold;
      display: block;
      margin-top: 10px;
    }

    .lease-calc-container input,
    .lease-calc-container select {
      width: 50%;
      padding: 8px;
      margin-top: 4px;
      margin-bottom: 12px;
      border: 1px solid #ccc;
      border-radius: 4px;
      box-sizing: border-box;
    }

    .lease-calc-container button {
      width: 50%;
      padding: 12px;
      background-color: #046172;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-size: 16px;
      margin-top: 10px;
    }

    .lease-calc-container p {
      margin-top: 20px;
      font-weight: bold;
      color: #333;
      text-align: center;
    }
  </style>
</head>
<body>

  <div class="lease-calc-container">
    <h3>Lease Renewal Cost Calculator</h3>

    <label for="location">Location:</label>
    <select id="location">
      <option value="selangor">Selangor</option>
      <option value="kl">Kuala Lumpur</option>
    </select>

    <label for="marketValue">Market Value of Land (RM/PSF):</label>
    <input type="number" id="marketValue" placeholder="e.g. 250" />

    <label for="yearsRemaining">Years Remaining on Lease:</label>
    <input type="number" id="yearsRemaining" placeholder="e.g. 35" />

    <label for="landSize">Land Size (sqft):</label>
    <input type="number" id="landSize" placeholder="e.g. 4000" />

    <button onclick="calculateLeaseRenewal()">Calculate</button>

    <p id="result"></p>
  </div>

  <script>
    function calculateLeaseRenewal() {
      const location = document.getElementById("location").value;
      const A = parseFloat(document.getElementById("marketValue").value);
      const B = parseFloat(document.getElementById("yearsRemaining").value);
      const C = parseFloat(document.getElementById("landSize").value);
      const resultEl = document.getElementById("result");

      if (isNaN(A) || isNaN(B) || isNaN(C) || B < 0 || B >= 99) {
        resultEl.innerText = "Please enter valid values. Years remaining must be between 0 and 98.";
        return;
      }

      let result = 0;

      if (location === "selangor") {
        result = (1/4) * (1/100) * A * (99 - B) * C;
      } else if (location === "kl") {
        result = (1/4) * A * (1/99) * (99 - B) * C;
      }

      resultEl.innerText = "Estimated Lease Renewal Cost: RM " + result.toFixed(2);
    }
  </script>

</body>
</html>
