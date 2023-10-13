---
layout: default
title: MortCanvas
---

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

        #assignmentDetails, #metadata {
            margin-top: 20px;
            border: 1px solid #ccc;
            padding: 10px;
            background-color: #fff;
            border-radius: 4px;
        }

        #metadata h2, #assignmentDetails h2 {
            margin-top: 0;
        }

        #iframeToggle {
            display: flex;
            align-items: center;
            cursor: pointer;
            margin-top: 20px;
        }

        #iframeArrow {
            color: blue;
            font-size: 24px;
            margin-right: 10px;
        }

        #assignmentIframe {
            width: 100%;
            height: 800px;
            border: none;
            border-radius: 4px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            display: none; /* Initially hidden */
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

<!-- Div to display metadata for the selected week -->
<div id="metadata">
    <h2>MortIt (QuickInfo):</h2>
    <!-- Metadata details will be dynamically populated -->
</div>

<!-- Toggle button for the iframe -->
<div id="iframeToggle" onclick="toggleIframe()">
    <span id="iframeArrow">➤</span>
    <span>View Assignment</span>
</div>

<!-- Iframe to display the content for the selected week -->
<iframe id="assignmentIframe"></iframe>

<script>
    // JavaScript object to store week details, iframe URLs, and metadata
    var weekDetails = {
        "week1": {
            "details": "Week 1: Java Hello, Java Console Games, Linux Shell and Bash",
            "iframeURL": "https://nighthawkcoders.github.io/teacher//c4.0/2023/08/15/java-hello_IPYNB_2_.html",
            "metadata": {
                "Hacks": "Build your own Jupyter Notebook meeting specific competencies.",
                "Due Date": "August 22, 2023",
                "Overall Assignment Objective": "Introduction to Java basics and Linux Shell."
            }
        },
        "week2": {
            "details": "Week 2: JS Calculator, JS Itunes API, JS Input, JS Output w/ jquery, JS Output w/ Objects",
            "iframeURL": "https://nighthawkcoders.github.io/teacher//c3.0/c3.1/c4.1/2023/09/06/javascript-output-jquery_IPYNB_2_.html",
            "metadata": {
                "Hacks": "Experiment with different JS libraries for enhanced functionality.",
                "Due Date": "September 13, 2023",
                "Overall Assignment Objective": "Introduction to JavaScript and jQuery."
            }
        },
        "week3": {
            "details": "Week 3: JavaScript Motion Dog",
            "iframeURL": "https://nighthawkcoders.github.io/teacher//2023/09/21/javascript_motion_dog_IPYNB_2_.html",
            "metadata": {
                "Hacks": "Animate the dog using CSS transitions.",
                "Due Date": "September 28, 2023",
                "Overall Assignment Objective": "Advanced JavaScript animations."
            }
        }
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
        var metadata = weekDetails[selectedWeek] ? weekDetails[selectedWeek].metadata : null;

        document.getElementById('assignmentDetails').innerText = details;

        // Display metadata if available
        var metadataDiv = document.getElementById('metadata');
        if (metadata) {
            metadataDiv.style.display = "block"; // Show metadata div
            metadataDiv.innerHTML = "<h2>Week Metadata:</h2>"; // Reset content
            for (var key in metadata) {
                metadataDiv.innerHTML += "<strong>" + key + ":</strong> " + metadata[key] + "<br>";
            }
        } else {
            metadataDiv.style.display = "none"; // Hide metadata div
        }

        document.getElementById('assignmentIframe').src = iframeURL;
    }

    function toggleIframe() {
        var iframe = document.getElementById('assignmentIframe');
        var arrow = document.getElementById('iframeArrow');
        if (iframe.style.display === "none") {
            iframe.style.display = "block";
            arrow.innerHTML = "➘";
        } else {
            iframe.style.display = "none";
            arrow.innerHTML = "➤";
        }
    }
</script>

</body>
</html>
