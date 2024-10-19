# energy air water usage calculation
#<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sustainable Smart City Dashboard</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 20px;
        }
        header {
            text-align: center;
            padding: 10px 0;
            background: #007BFF;
            color: white;
        }
        .dashboard {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
        }
        .card {
            background: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            padding: 20px;
            margin: 10px;
            flex: 1 1 200px;
            min-width: 250px;
        }
        .card h2 {
            margin: 0 0 10px;
        }
        .chart {
            height: 100px;
            background: #e9ecef;
            border-radius: 4px;
            position: relative;
        }
        .chart div {
            height: 100%;
            background: #007BFF;
            position: absolute;
            bottom: 0;
            transition: height 0.3s ease;
        }
    </style>
</head>
<body>

<header>
    <h1>Sustainable Smart City Dashboard</h1>
</header>

<div class="dashboard">
    <div class="card">
        <h2>Energy Efficiency</h2>
        <div class="chart">
            <div style="width: 70%;"></div>
        </div>
        <p>Energy usage: 70%</p>
    </div>
    
    <div class="card">
        <h2>Air Quality</h2>
        <div class="chart">
            <div style="width: 80%;"></div>
        </div>
        <p>Air Quality Index: 80</p>
    </div>
    
    <div class="card">
        <h2>Traffic Flow</h2>
        <div class="chart">
            <div style="width: 50%;"></div>
        </div>
        <p>Traffic congestion: 10%</p>
    </div>

    <div class="card">
        <h2>Water Usage</h2>
        <div class="chart">
            <div style="width: 60%;"></div>
        </div>
        <p>Water usage: 60%</p>
    </div>
</div>

<script>
    // Example function to simulate updating data
    function updateData() {
        const energy = Math.floor(Math.random() * 100);
        const airQuality = Math.floor(Math.random() * 100);
        const traffic = Math.floor(Math.random() * 100);
        const water = Math.floor(Math.random() * 100);

        document.querySelector('.dashboard .card:nth-child(1) .chart div').style.width = energy + '%';
        document.querySelector('.dashboard .card:nth-child(1) p').textContent = 'Energy usage: ' + energy + '%';
        
        document.querySelector('.dashboard .card:nth-child(2) .chart div').style.width = airQuality + '%';
        document.querySelector('.dashboard .card:nth-child(2) p').textContent = 'Air Quality Index: ' + airQuality;

        document.querySelector('.dashboard .card:nth-child(3) .chart div').style.width = traffic + '%';
        document.querySelector('.dashboard .card:nth-child(3) p').textContent = 'Traffic congestion: ' + traffic + '%';

        document.querySelector('.dashboard .card:nth-child(4) .chart div').style.width = water + '%';
        document.querySelector('.dashboard .card:nth-child(4) p').textContent = 'Water usage: ' + water + '%';
    }

    // Update data every 5 seconds
    setInterval(updateData, 5000);
</script>

</body>
</html>

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
