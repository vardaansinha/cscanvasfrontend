---
layout: blogs
permalink: /login
title: Login Page
---

# Simple Frontend Login Page

## HTML (login.html)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="styles.css">
    <title>Login Page</title>
</head>
<body>
    <div class="login-container">
        <h2>Welcome to Our Platform</h2>
        <div class="input-group">
            <label for="key">Teacher Key:</label>
            <input type="password" id="key" placeholder="Enter teacher key...">
        </div>
        <button onclick="loginAsTeacher()">Login as Teacher</button>
        <div class="divider">
            <span>OR</span>
        </div>
        <button onclick="loginAsStudent()">Login as Student</button>
    </div>
    <script src="script.js"></script>
</body>
</html>


<style>

body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f4f4f4;
}

.login-container {
    background-color: #fff;
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
    width: 300px;
    text-align: center;
}

.input-group {
    margin-bottom: 10px;
}

label {
    display: block;
    margin-bottom: 5px;
}

input[type="password"] {
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


<script>

function loginAsTeacher() {
    const key = document.getElementById('key').value;
    if (key === "SPECIFIC_TEACHER_KEY") {
        alert("Logged in as a teacher!");
    } else {
        alert("Invalid key!");
    }
}

function loginAsStudent() {
    alert("Logged in as a student!");
}


</script>