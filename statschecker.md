<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Student GitHub Stats</title>
<style>
 /* Base styling */
  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
    text-align: center;
  }
  /* Header styling */
  h2 {
    color: #333;
  }
  /* Dropdown styling */
  select {
    padding: 10px;
    margin-top: 20px;
    font-size: 16px;
  }
  /* Container for stats */
  #stats {
    background-color: #fff;
    border-radius: 5px;
    box-shadow: 0 0 3px rgba(0, 0, 0, 0.1);
    margin: 20px auto;
    padding: 20px;
    width: 90%;
    max-width: 400px;
  }
  /* Stat list styling */
  p {
    font-size: 18px;
    line-height: 2;
    text-align: left;
    padding-left: 20px;
    border-left: 3px solid #4CAF50; /* a nice green */
  }
  /* Strong tag styling */
  strong {
    color: #333;
  }
</style>
</head>
<html>
<h1> CSA Student Stats Checker - MortCanvas.org </h1>
<body>

<!-- Dropdown selection for the student list -->
<select id="studentList" onchange="showStats()">
  <option value="">--Select a Student--</option>
  <option value="Edwin Abraham">Edwin Abraham</option>
  <option value="Vishnu Aravind">Vishnu Aravind</option>
  <option value="Anthony Bazhenov">Anthony Bazhenov</option>
    <option value="Quinn Bireley">Quinn Bireley</option>
  <option value="Orlando Carcamo">Orlando Carcamo</option>
  <option value="Finn Carpenter">Finn Carpenter</option>
  <option value="Aniket Chakradeo">Aniket Chakradeo</option>
  <option value="Nikhil Chakravarthula">Nikhil Chakravarthula</option>
  <option value="Matiullah Danish">Matiullah Danish</option>
  <option value="Kaiden Do">Kaiden Do</option>
  <option value="Kevin Du">Kevin Du</option>
  <option value="Sreeja Reddy Gangapuram">Sreeja Reddy Gangapuram</option>
  <option value="Shaurya Goel">Shaurya Goel</option>
  <option value="Shivansh Goel">Shivansh Goel</option>
  <option value="Isabelle Gunawan">Isabelle Gunawan</option>
  <option value="Derrick Huang">Derrick Huang</option>
  <option value="Theodore Huntalas">Theodore Huntalas</option>
  <option value="Aiden Huynh">Aiden Huynh</option>
  <option value="Luna Iwazaki">Luna Iwazaki</option>
  <option value="Rachit Jaiswal">Rachit Jaiswal</option>
  <option value="Ekamjot Kaire">Ekamjot Kaire</option>
  <option value="Soham Kamat">Soham Kamat</option>
  <option value="Tay Kim">Tay Kim</option>
  <option value="Jeongwoo Lee">Jeongwoo Lee</option>
  <option value="Toby Leeder">Toby Leeder</option>
  <option value="Alexander Lu">Alexander Lu</option>
  <option value="Krishiv Mahendru">Krishiv Mahendru</option>
  <option value="Ryan McWeeny">Ryan McWeeny</option>
  <option value="Emaad Mir">Emaad Mir</option>
  <option value="Raunak Mondal">Raunak Mondal</option>
  <option value="John Mortensen">John Mortensen</option>
  <option value="Aditya Nawandhar">Aditya Nawandhar</option>
  <option value="Justin Nguyen">Justin Nguyen</option>
  <option value="Vivian Ni">Vivian Ni</option>
  <option value="Varaprasad Nibhanupudi">Varaprasad Nibhanupudi</option>
  <option value="Akshat Parikh">Akshat Parikh</option>
  <option value="Tanay Patel">Tanay Patel</option>
  <option value="Tanisha Patil">Tanisha Patil</option>
  <option value="Paaras Purohit">Paaras Purohit</option>
  <!-- List of students -->
  <!-- ... your list of students ... -->
</select>

<div id="stats">
  <!-- GitHub stats will be displayed here -->
</div>

<script>
  function getRandomStat(max = 500) {
    // Function to generate a random stat value up to a maximum, defaulting to 500
    return Math.floor(Math.random() * max) + 1; // random number up to 'max', minimum 1
  }

  function showStats() {
    const student = document.getElementById("studentList").value;
    
    if (student) {
      // Generate random stats for the selected student
      const stats = `
        <h2>${student}'s GitHub Stats</h2>
        <p><strong>Commits:</strong> ${getRandomStat()}</p>
        <p><strong>Repositories Contributed To:</strong> ${getRandomStat(10)}</p> <!-- Limit to 1-10 -->
        <p><strong>Additions:</strong> ${getRandomStat()}</p>
        <p><strong>Deletions:</strong> ${getRandomStat()}</p>
      `;

      // Display the stats in the 'stats' div
      document.getElementById("stats").innerHTML = stats;
    } else {
      // If no student is selected, clear the displayed stats
      document.getElementById("stats").innerHTML = '';
    }
  }
</script>

</body>
</html>
