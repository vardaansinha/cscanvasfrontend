---
permalink: /stats
title: Stats Page
---

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
<select id="studentList" onchange="showStats(this.value)">
  <option value="">--Select a Student--</option>
  {% for student in site.data.students %}
    <option value="{{ student.name }}">{{ student.name }}</option>
  {% endfor %}
</select>

<div id="stats">
  <!-- GitHub stats will be displayed here -->
</div>

<script>

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
