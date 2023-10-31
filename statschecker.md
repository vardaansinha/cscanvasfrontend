<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Stats Input</title>
    <link rel="stylesheet" href="styles.css">
</head>
<style>
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
}
.container {
    max-width: 500px;
    margin: 50px auto;
    background-color: #fff;
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
h1 {
    text-align: center;
    margin-bottom: 20px;
}
.input-group {
    margin-bottom: 20px;
}
label {
    display: block;
    margin-bottom: 5px;
}
input {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
}
button {
    display: block;
    width: 100%;
    padding: 10px;
    background-color: #007BFF;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}
button:hover {
    background-color: #0056b3;
}
</style>
<body>
    <div class="container">
        <h1>Enter Your GitHub Stats</h1>
        <form id="githubStatsForm">
            <div class="input-group">
                <label for="commits">Commits:</label>
                <input type="number" id="commits" required>
            </div>
            <div class="input-group">
                <label for="pulls">Pull Requests:</label>
                <input type="number" id="pulls" required>
            </div>
            <div class="input-group">
                <label for="issues">Issues:</label>
                <input type="number" id="issues" required>
            </div>
            <div class="input-group">
                <label for="repos">Repositories Contributed To:</label>
                <input type="number" id="repos" required>
            </div>
            <button type="submit">Submit</button>
        </form>
    </div>
    <script src="script.js">
    // Define the API endpoint URL
const apiUrl = '/api/grade/predict'; // Adjust the URL as needed
// Create an object to store your request data
const requestData = {
    numStudents: 10 // Replace with your desired value
};
// Define the fetch options, including the HTTP method and headers
const fetchOptions = {
    method: 'POST', // Use POST since you are sending data in the request body
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify(requestData) // Convert request data to JSON
};
// Make the API request using the fetch function
fetch(apiUrl, fetchOptions)
    .then(response => {
        if (!response.ok) {
            throw new Error('Network response was not ok');
        }
        return response.json(); // Parse the response as JSON
    })
    .then(data => {
        // Handle the response data here
        console.log('API Response:', data);
        // You can access the computation and imageUrls in the 'data' object
        // For example, you can display the computation string and image URLs in your HTML.
        document.getElementById('computation').textContent = data.computation;
        const imageUrls = data.imageUrls;
        imageUrls.forEach(url => {
            const img = document.createElement('img');
            img.src = url;
            document.getElementById('imageContainer').appendChild(img);
        });
    })
    .catch(error => {
        console.error('Error:', error);
        // Handle errors here
    });
11:20
chang
    </script>
</body>
</html>
