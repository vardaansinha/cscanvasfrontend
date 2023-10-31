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
<body>
  <h1>CSA Student Stats Checker - MortCanvas.org</h1>

  <!-- Dropdown selection for the student list -->
  <select id="studentList">
    <option value="">--Select a Student--</option>
    {% for student in site.data.students %}
      <option value="{{ student.name }}">{{ student.name }}</option>
    {% endfor %}
  </select>

  <div id="stats">
    <!-- GitHub stats will be displayed here -->
  </div>

  <script>
    // Define an object to encapsulate the functionality
    const StudentStatsApp = {
      students: [],

      // Initialize the application
      init: function () {
        // Convert the Liquid student data into a format that JavaScript can read
        this.students = {{ site.data.students | jsonify }};

        // Attach the showStats function to the dropdown's onchange event
        const studentList = document.getElementById("studentList");
        studentList.onchange = this.showStats.bind(this, studentList);

        // Initialize with the default option selected
        this.showStats(studentList);
      },

      // This function is called whenever a user selects a student from the dropdown
      showStats: function (selectElement) {
        const studentName = selectElement.value;
        const student = this.students.find(s => s.name === studentName);

        // Create the stats display using the student data
        let stats = "<h2>GitHub Stats</h2>";

        if (student) {
          stats += `
            <h2>${student.name}'s GitHub Stats</h2>
            <p><strong>Commits:</strong> ${student.commits}</p>
            <p><strong>Repositories Contributed To:</strong> ${student.repositories}</p>
            <p><strong>Additions:</strong> ${student.additions}</p>
            <p><strong>Deletions:</strong> ${student.deletions}</p>
          `;
        }

        // Display the stats in the 'stats' div
        const statsElement = document.getElementById("stats");
        statsElement.innerHTML = stats;
      },
    };

    // Initialize the application when the DOM is ready
    document.addEventListener("DOMContentLoaded", function () {
      StudentStatsApp.init();
    });
  </script>
</body>
</html>
