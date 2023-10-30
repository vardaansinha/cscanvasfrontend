<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Signup Page</title>
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

        .signup-container {
            background-color: #fff;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 400px;
            text-align: center;
        }

        .input-group {
            margin-bottom: 10px;
        }

        label {
            display: block;
            margin-bottom: 5px;
        }

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
    </style>
</head>

<body>
    <div class="signup-container">
        <h2>Welcome to MortCanvas</h2>
        <div class="input-group">
            <label for="name">Name:</label>
            <input type="text" id="name" placeholder="Enter your name...">
        </div>
        <div class="input-group">
            <label for="id">ID:</label>
            <input type="text" id="id" placeholder="Enter your ID...">
        </div>
        <button onclick="signup()">Sign Up</button>
    </div>

    <script>
        function signup() {
            const name = document.getElementById('name').value;
            const id = document.getElementById('id').value;

            if (name && id) {
                fetchSignup(id, name);
            } else {
                alert("Please fill out all fields.");
            }
        }

        async function fetchSignup(id, name) {
            try {
                const response = await fetch(`http://localhost:8085/api/signup?id=${id}&name=${name}`);
                const data = await response.json();

                if (data.isTeacher) {
                    window.location.href = "https://vardaansinha.github.io/cscanvasfrontend/teacher";
                } else if (data.isStudent) {
                    window.location.href = "https://vardaansinha.github.io/cscanvasfrontend/index";
                } else {
                    alert("Signup unsuccessful. Invalid ID.");
                }
            } catch (error) {
                alert("An error occurred while signing up.");
            }
        }
    </script>
</body>

</html>
