#smart city management(waste management calculation)
# html code
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Waste Management Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
    }
  </style>
</head>
<body>
  <h1>Waste Management Calculator</h1>
  <form onsubmit="return false;">
    <label>Waste Generation Rate (kg/day):</label>
    <input type="number" id="waste-generation" value="100" required><br><br>
    <label>Waste Collection Frequency (days):</label>
    <input type="number" id="collection-frequency" value="3" required><br><br>
    <label>Organic Waste Percentage (%):</label>
    <input type="number" id="organic-percentage" value="30" required><br><br>
    <label>Recyclable Waste Percentage (%):</label>
    <input type="number" id="recyclable-percentage" value="20" required><br><br>
    <button onclick="calculateWaste(event)">Calculate</button>
  </form>
  <div id="results"></div>

  <script>
    function calculateWaste(event) {
      event.preventDefault(); // Prevent form submission

      const wasteGeneration = parseFloat(document.getElementById('waste-generation').value);
      const collectionFrequency = parseFloat(document.getElementById('collection-frequency').value);
      const organicPercentage = parseFloat(document.getElementById('organic-percentage').value);
      const recyclablePercentage = parseFloat(document.getElementById('recyclable-percentage').value);

      // Calculate total waste generated per collection
      const totalWaste = wasteGeneration * collectionFrequency;

      // Calculate organic waste
      const organicWaste = (totalWaste * organicPercentage) / 100;

      // Calculate recyclable waste
      const recyclableWaste = (totalWaste * recyclablePercentage) / 100;

      // Calculate non-recyclable waste
      const nonRecyclableWaste = totalWaste - organicWaste - recyclableWaste;

      // Display results
      const results = `
        <h2>Results:</h2>
        <p>Total Waste Generated: ${totalWaste.toFixed(2)} kg</p>
        <p>Organic Waste: ${organicWaste.toFixed(2)} kg (${organicPercentage}%)</p>
        <p>Recyclable Waste: ${recyclableWaste.toFixed(2)} kg (${recyclablePercentage}%)</p>
        <p>Non-Recyclable Waste: ${nonRecyclableWaste.toFixed(2)} kg</p>
      `;
      document.getElementById('results').innerHTML = results;
    }
  </script>
</body>
</html>
