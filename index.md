---
layout: default
title: Student Blog
---
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MortCanvas Assignment Selector</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            padding: 20px;
            background-color: #f4f4f4;
        }
        label, select {
            margin-bottom: 20px;
        }
        select {
            padding: 10px;
            width: 100%;
            border: 1px solid #ccc;
            border-radius: 4px;
            font-size: 16px;
        }
        #assignmentDetails {
            margin-top: 20px;
            border: 1px solid #ccc;
            padding: 10px;
            background-color: #fff;
            border-radius: 4px;
        }
        #assignmentIframe {
            width: 100%;
            height: 800px;
            border: none;
            border-radius: 4px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        h1 {
            color: #333;
        }
        #toggleIframeBtn {
            display: flex;
            align-items: center;
            cursor: pointer;
            color: blue;
            margin-top: 10px;
        }
        #toggleArrow {
            border: solid blue;
            border-width: 0 3px 3px 0;
            display: inline-block;
            padding: 3px;
            transform: rotate(-45deg);
            transition: transform 0.3s;
        }
        #assignmentIframe.collapsed {
            display: none;
        }
    </style>
</head>
<body>

<h1>Assignment Selector</h1>

<!-- Dropdown for selecting an assignment week -->
<label for="week">Assignment Week:</label>
<select id="week" name="week" onchange="displayAssignment()">
    <option value="">Select a Week</option>
    <!-- Options will be dynamically populated -->
</select>

<!-- Dropdown for selecting an assignment category -->
<label for="category">Assignment Category:</label>
<select id="category" name="category">
    <option value="homework">Homework</option>
    <option value="project">Project</option>
    <option value="exam">Exam</option>
    <!-- Add more categories as needed -->
</select>

<!-- Div to display the selected assignment details -->
<div id="assignmentDetails"></div>

<!-- Button to toggle the iframe visibility -->
<div id="toggleIframeBtn" onclick="toggleIframe()">
    <div id="toggleArrow"></div>
    View Assignment Content
</div>

<!-- Iframe to display the content for the selected week -->
<iframe id="assignmentIframe" class="collapsed"></iframe>

<script>
    // JavaScript object to store week details and iframe URLs
    var weekDetails = {
        "week1": {
            "details": "Week 1: Java Hello, Java Console Games, Linux Shell and Bash",
            "iframeURL": "https://nighthawkcoders.github.io/teacher//c4.0/2023/08/15/java-hello_IPYNB_2_.html"
        },
        "week2": {
            "details": "Week 2: JS Calculator, JS Itunes API, JS Input, JS Output w/ jquery, JS Output w/ Objects",
            "iframeURL": "https://nighthawkcoders.github.io/teacher//c3.0/c3.1/c4.1/2023/09/06/javascript-output-jquery_IPYNB_2_.html"
        },
        "week3": {
            "details": "Week 3: JavaScript Motion Dog",
            "iframeURL": "https://nighthawkcoders.github.io/teacher//2023/09/21/javascript_motion_dog_IPYNB_2_.html"
        }
        // ... Add more weeks and their details
    };

    // Dynamically populate the dropdown with weeks
    var weekSelector = document.getElementById('week');
    for (var week in weekDetails) {
        var option = document.createElement('option');
        option.value = week;
        option.text = week.charAt(0).toUpperCase() + week.slice(1);  // Convert "week1" to "Week1"
        weekSelector.appendChild(option);
    }

    function displayAssignment() {
        var selectedWeek = weekSelector.value;
        var details = weekDetails[selectedWeek] ? weekDetails[selectedWeek].details : "Please select a valid week.";
        var iframeURL = weekDetails[selectedWeek] ? weekDetails[selectedWeek].iframeURL : "";

        document.getElementById('assignmentDetails').innerText = details;
        document.getElementById('assignmentIframe').src = iframeURL;
    }

    function toggleIframe() {
        var iframe = document.getElementById('assignmentIframe');
        var arrow = document.getElementById('toggleArrow');
        if (iframe.classList.contains('collapsed')) {
            iframe.classList.remove('collapsed');
            arrow.style.transform = 'rotate(135deg)';
        } else {
            iframe.classList.add('collapsed');
            arrow.style.transform = 'rotate(-45deg)';
        }
    }
</script>

</body>
</html>
