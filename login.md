<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
            margin: 0;
        }

        .login-container {
            background-color: #fff;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 400px; /* Adjusted this to not take up the entire viewport width */
            text-align: center;
        }

        .input-group {
            margin-bottom: 10px;
        }

        label {
            display: block;
            margin-bottom: 5px;
        }

        input[type="password"],
        input[type="text"] {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }

        button {
            padding: 10px 15px;
            border: none;
            background-color: #007BFF;
            color: #fff;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 10px;
        }

        button:hover {
            background-color: #0056b3;
        }

        .divider {
            margin: 20px 0;
            position: relative;
        }

        .divider span {
            background-color: #fff;
            position: relative;
            z-index: 1;
            padding: 0 10px;
        }

        .divider::before {
            content: "";
            position: absolute;
            top: 50%;
            left: 0;
            right: 0;
            height: 1px;
            background-color: #ddd;
        }
    </style>
</head>

<body>
    <div class="login-container">
        <h2>Welcome to MortCanvas</h2>
        <div class="input-group">
            <label for="key">Teacher Key:</label>
            <input type="password" id="key" placeholder="Enter teacher key...">
        </div>
        <button onclick="loginAsTeacher()">Login as Teacher</button>

        <div class="divider">
            <span>OR</span>
        </div>

        <div class="input-group">
            <label for="studentID">Student ID:</label>
            <input type="text" id="studentID" placeholder="Enter 7 digit ID...">
        </div>
        <button onclick="loginAsStudent()">Login as Student</button>
    </div>

    <script>
        function loginAsTeacher() {
            const key = document.getElementById('key').value;
            if (key === "MortCSA") {
                window.location.href = "https://vardaansinha.github.io/cscanvasfrontend/teacher";
            } else {
                alert("Invalid teacher key!");
            }
        }

        function loginAsStudent() {
            const studentID = document.getElementById('studentID').value;
            if (studentID.length === 7 && !isNaN(studentID)) {  // checks if input is a 7 digit number
                window.location.href = "https://vardaansinha.github.io/cscanvasfrontend/";
            } else {
                alert("Invalid student ID! Please enter a 7-digit number.");
            }
        }
    </script>
</body>

</html>
