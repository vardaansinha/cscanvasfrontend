<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSCanvas Assignment Selector</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            padding: 20px;
            background-color: #f4f4f4;
            color: #001F3F; /* Navy */
        }

        h1, h2 {
            color: #001F3F; /* Navy */
        }

        label, select {
            margin-bottom: 20px;
        }

        select {
            padding: 10px;
            width: 100%;
            border: 1px solid #001F3F; /* Navy */
            border-radius: 4px;
            font-size: 16px;
            color: #001F3F; /* Navy */
            background-color: white;
        }

        #assignmentDetails, #metadata {
            margin-top: 20px;
            border: 1px solid #001F3F; /* Navy */
            padding: 10px;
            background-color: #fff;
            border-radius: 4px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        #iframeToggle {
            display: flex;
            align-items: center;
            cursor: pointer;
            margin-top: 20px;
            padding: 10px;
            border-radius: 4px;
            background-color: #001F3F; /* Navy */
            color: white;
            transition: background-color 0.3s;
        }

        #iframeToggle:hover {
            background-color: #003366; /* Darker Navy */
        }

        #iframeArrow {
            font-size: 24px;
            margin-right: 10px;
            transition: transform 0.3s;
        }

        #assignmentIframe {
            width: 100%;
            height: 800px;
            border: none;
            border-radius: 4px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            display: none; /* Initially hidden */
        }

        /* Calendar Styles */
        .calendar {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 10px;
            margin-bottom: 20px;
        }

        .calendar button {
            padding: 10px;
            border: none;
            border-radius: 4px;
            background-color: #001F3F; /* Navy */
            color: white;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .calendar button:hover {
            background-color: #003366; /* Darker Navy */
        }

        .calendar button.active {
            background-color: #0074D9; /* Blue */
        }
    </style>
</head>

<body>

<h1>Welcome CS Learner!</h1>

<!-- Calendar -->
<div class="calendar">
    <button onclick="selectWeek('week1')">Week 1</button>
    <button onclick="selectWeek('week2')">Week 2</button>
    <button onclick="selectWeek('week3')">Week 3</button>
    <button onclick="selectWeek('week4')">Week 4</button>
    <button onclick="selectWeek('week5')">Week 5</button>
    <button onclick="selectWeek('week6')">Week 6</button>
    <button onclick="selectWeek('week7')">Week 7</button>
</div>

<label for="week">Assignment Week:</label>
<select id="week" name="week"></select>

<label for="category">Assignment Category:</label>
<select id="category" name="category">
    <option value="homework">Homework</option>
    <option value="project">Project</option>
    <option value="exam">Exam</option>
</select>

<div id="assignmentDetails"></div>
<div id="metadata">
    <h2>MortIt (QuickInfo):</h2>
</div>
<div id="iframeToggle" onclick="assignmentManager.toggleIframe()">
    <span id="iframeArrow">➤</span>
    <span>View Assignment</span>
</div>
<iframe id="assignmentIframe"></iframe>

<script>
class Assignment {
    constructor(details, iframeURL, metadata) {
        this.details = details;
        this.iframeURL = iframeURL;
        this.metadata = metadata;
    }
}

class AssignmentManager {
    constructor() {
        this.weekDetails = {
            "week1": new Assignment(
                "Week 1: Java Hello, Java Console Games, Linux Shell and Bash",
                "https://nighthawkcoders.github.io/teacher//c4.0/2023/08/15/java-hello_IPYNB_2_.html",
                {
                    "Hacks": "Build your own Jupyter Notebook meeting specific competencies.",
                    "Due Date": "August 22, 2023",
                    "Overall Assignment Objective": "Introduction to Java basics and Linux Shell."
                }
            ),
            "week2": new Assignment(
                "Week 2: JS Calculator, JS Itunes API, JS Input, JS Output w/ jquery, JS Output w/ Objects",
                "https://nighthawkcoders.github.io/teacher//c3.0/c3.1/c4.1/2023/09/06/javascript-output-jquery_IPYNB_2_.html",
                {
                    "Hacks": "Experiment with different JS libraries for enhanced functionality.",
                    "Due Date": "September 13, 2023",
                    "Overall Assignment Objective": "Introduction to JavaScript and jQuery."
                }
            ),
            "week3": new Assignment(
                "Week 3: JavaScript Motion Dog",
                "https://nighthawkcoders.github.io/teacher//2023/09/21/javascript_motion_dog_IPYNB_2_.html",
                {
                    "Hacks": "Animate the dog using CSS transitions.",
                    "Due Date": "September 28, 2023",
                    "Overall Assignment Objective": "Advanced JavaScript animations."
                }
            ),
            "week4": new Assignment(
                "Week 4: Student Teaching Tri 1",
                "https://nighthawkcoders.github.io/teacher//2023/09/28/java-student-teach-tri1.html",
                {
                    "Hacks": "Engage in peer teaching and learn from fellow students.",
                    "Due Date": "October 5, 2023",
                    "Overall Assignment Objective": "Peer teaching and collaborative learning."
                }
            ),
            "week5": new Assignment(
                "Week 5: ChatGPT in Java",
                "https://nighthawkcoders.github.io/teacher//2023/10/09/java-chatgpt_IPYNB_2_.html",
                {
                    "Hacks": "Integrate ChatGPT with Java applications.",
                    "Due Date": "October 16, 2023",
                    "Overall Assignment Objective": "Introduction to ChatGPT in Java."
                }
            ),
            "week6": new Assignment(
                "Week 6: Passion Project Tri 1",
                "https://nighthawkcoders.github.io/teacher//2023/09/28/java-spring_passion.html",
                {
                    "Hacks": "Work on a project of your choice and showcase your skills.",
                    "Due Date": "October 23, 2023",
                    "Overall Assignment Objective": "Self-directed project work."
                }
            ),
            "week7": new Assignment(
                "Week 7: PP Ideation Checkpoint",
                "https://nighthawkcoders.github.io/teacher//2023/09/28/java-spring-passion-idea.html",
                {
                    "Hacks": "Brainstorm and finalize your project idea.",
                    "Due Date": "October 30, 2023",
                    "Overall Assignment Objective": "Project ideation and planning."
                }
            )
        };
        this.populateWeekDropdown();
        document.getElementById('week').addEventListener('change', () => this.displayAssignment());
    }

    populateWeekDropdown() {
        const weekSelector = document.getElementById('week');
        for (const week in this.weekDetails) {
            const option = document.createElement('option');
            option.value = week;
            option.text = week.charAt(0).toUpperCase() + week.slice(1);
            weekSelector.appendChild(option);
        }
    }

    displayAssignment() {
        const selectedWeek = document.getElementById('week').value;
        const assignment = this.weekDetails[selectedWeek];
        document.getElementById('assignmentDetails').innerText = assignment ? assignment.details : "Please select a valid week.";
        document.getElementById('assignmentIframe').src = assignment ? assignment.iframeURL : "";

        const metadataDiv = document.getElementById('metadata');
        if (assignment && assignment.metadata) {
            metadataDiv.style.display = "block";
            metadataDiv.innerHTML = "<h2>Week Metadata:</h2>";
            for (const key in assignment.metadata) {
                metadataDiv.innerHTML += `<strong>${key}:</strong> ${assignment.metadata[key]}<br>`;
            }
        } else {
            metadataDiv.style.display = "none";
        }
    }

    toggleIframe() {
        const iframe = document.getElementById('assignmentIframe');
        const arrow = document.getElementById('iframeArrow');
        if (iframe.style.display === "none") {
            iframe.style.display = "block";
            arrow.innerHTML = "➘";
        } else {
            iframe.style.display = "none";
            arrow.innerHTML = "➤";
        }
    }
}

const assignmentManager = new AssignmentManager();

function selectWeek(week) {
    document.getElementById('week').value = week;
    assignmentManager.displayAssignment();
}
</script>

</body>

</html>
