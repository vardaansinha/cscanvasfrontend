<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Assignment Checker & Turn-In Platform</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            padding: 20px;
        }

        .button {
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            margin-top: 10px;
        }

        .button-blue {
            background-color: blue;
            color: white;
        }

        .button-green {
            background-color: green;
            color: white;
        }

        .input-field {
            margin-bottom: 20px;
        }

        .input-field label {
            display: block;
            margin-bottom: 5px;
        }

        .input-field input[type="text"],
        .input-field select,
        .input-field input[type="number"] {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            border: 1px solid #aaa;
        }

        table, th, td {
            border: 1px solid #aaa;
        }

        th, td {
            padding: 10px;
            text-align: left;
        }

        th {
            background-color: #f5f5f5;
        }

        h2 {
            text-align: center;
            margin-top: 40px;
        }

        #assignmentForm {
            margin-top: 20px;
        }

        .edit-btn {
            background-color: transparent;
            border: none;
            cursor: pointer;
            font-size: 1.5rem;
            color: #007BFF;
        }
    </style>
</head>

<body>

<button class="button button-blue" onclick="showForm()">+ New Assignment</button>

<div id="assignmentForm" style="display: none;">
    <div class="input-field">
        <label for="title">Title of Assignment:</label>
        <input type="text" id="title" name="title">
    </div>

    <div class="input-field">
        <label for="description">Description of Assignment:</label>
        <input type="text" id="description" name="description">
    </div>

    <div class="input-field">
        <label for="category">Assignment Category:</label>
        <select id="category" name="category">
            <option value="homework">Homework</option>
            <option value="project">Project</option>
            <option value="exam">Exam</option>
        </select>
    </div>

    <div class="input-field">
        <label for="week">Assignment Week:</label>
        <select id="week" name="week">
            <option value="Week 1">Week 1</option>
            <option value="Week 2">Week 2</option>
            <option value="Week 3">Week 3</option>
            <option value="Week 4">Week 4</option>
            <option value="Week 5">Week 5</option>
            <option value="Week 6">Week 6</option>
          <option value="Week 7">Week 7</option>
          <option value="Week 8">Week 8</option>
          <option value="Week 9">Week 9</option>
          <option value="Week 10">Week 10</option>
          <option value="Week 11">Week 11</option>
          <option value="Week 12">Week 12</option>
          <option value="Week 13">Week 13</option>
          <option value="Week 14">Week 14</option>
          <option value="Week 15">Week 15</option>
          <option value="Week 16">Week 16</option>
          <option value="Week 17">Week 17</option>
          <option value="Week 18">Week 18</option>
          <option value="Week 19">Week 19</option>
          <option value="Week 20">Week 20</option>
          <option value="Week 21">Week 21</option>
          <option value="Week 22">Week 22</option>
          <option value="Week 23">Week 23</option>
          <option value="Week 24">Week 24</option>
          <option value="Week 25">Week 25</option>
          <option value="Week 26">Week 26</option>
          <option value="Week 27">Week 27</option>
          <option value="Week 28">Week 28</option>
          <option value="Week 29">Week 29</option>
          <option value="Week 30">Week 30</option>
          <option value="Week 31">Week 31</option>
          <option value="Week 32">Week 32</option>
          <option value="Week 33">Week 33</option>
          <option value="Week 34">Week 34</option>
            <option value="Week 35">Week 35</option>
            <option value="Week 36">Week 36</option>
        </select>
    </div>

    <div class="input-field">
        <label for="points">Points:</label>
        <input type="number" id="points" name="points">
    </div>

    <button class="button button-green" onclick="saveAssignment()">Save</button>
</div>

<h2>Your Published Assignments</h2>
<div id="savedAssignments"></div>

<script>
    let currentEditIndex = null;

    function showForm() {
        document.getElementById('assignmentForm').style.display = 'block';
    }

    function saveAssignment() {
        let assignments = localStorage.getItem('assignments');
        assignments = assignments ? JSON.parse(assignments) : [];
        
        let assignment = {
            title: document.getElementById('title').value,
            description: document.getElementById('description').value,
            category: document.getElementById('category').value,
            week: document.getElementById('week').value,
            points: document.getElementById('points').value
        };

        if (currentEditIndex !== null) {
            assignments[currentEditIndex] = assignment;
            currentEditIndex = null;
        } else {
            assignments.push(assignment);
        }
        
        localStorage.setItem('assignments', JSON.stringify(assignments));
        displayAssignments();
        document.getElementById('assignmentForm').style.display = 'none'; // Hide the form after saving

        alert('Assignment saved!');
    }

    function editAssignment(index) {
        const assignments = JSON.parse(localStorage.getItem('assignments'));
        const assignment = assignments[index];

        document.getElementById('title').value = assignment.title;
        document.getElementById('description').value = assignment.description;
        document.getElementById('category').value = assignment.category;
        document.getElementById('week').value = assignment.week;
        document.getElementById('points').value = assignment.points;

        currentEditIndex = index;

        showForm();
    }

    function displayAssignments() {
        let assignments = localStorage.getItem('assignments');
        assignments = assignments ? JSON.parse(assignments) : [];

        let tableHtml = `
        <table>
            <thead>
                <tr>
                    <th>Title</th>
                    <th>Description</th>
                    <th>Category</th>
                    <th>Week</th>
                    <th>Points</th>
                    <th>Edit</th>
                </tr>
            </thead>
            <tbody>
        `;

        assignments.forEach((assignment, index) => {
            tableHtml += `
                <tr>
                    <td>${assignment.title}</td>
                    <td>${assignment.description}</td>
                    <td>${assignment.category}</td>
                    <td>${assignment.week}</td>
                    <td>${assignment.points}</td>
                    <td><button class="edit-btn" onclick="editAssignment(${index})">✏️</button></td>
                </tr>
            `;
        });

        tableHtml += '</tbody></table>';
        document.getElementById('savedAssignments').innerHTML = tableHtml;
    }

    window.onload = function() {
        displayAssignments();
    };

</script>

</body>

</html>
