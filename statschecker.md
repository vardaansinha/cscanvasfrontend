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
        <div id="computation"></div>
        <div id="imageContainer"></div>
    </div>
   <script>
    // Define the API endpoint URL
    const apiUrl = 'http://cscanvas.stu.nighthawkcodingsociety.com/api/grade/predict';

    document.getElementById('githubStatsForm').addEventListener('submit', function(event) {
        event.preventDefault();

        // Get values from the form
        const commits = document.getElementById('commits').value;
        const pulls = document.getElementById('pulls').value;
        const issues = document.getElementById('issues').value;
        const repos = document.getElementById('repos').value;

        // Create an object to store your request data
        const requestData =
            {
                "numStudents": 1000
            }

        // Define the fetch options, including the HTTP method and headers
        const fetchOptions = {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify(requestData)
        };

        // Make the API request using the fetch function
        fetch(apiUrl, fetchOptions)
            .then(response => {
                if (!response.ok) {
                    throw new Error('Network response was not ok');
                }
                return response.json();
            })
            .then(data => {
                // Compute the prediction using the returned coefficients
                const prediction = data.bias
                                   (data.commitCoefficient * commits) + 
                                   (data.pullCoefficient * pulls) + 
                                   (data.issueCoefficient * issues) + 
                                   (data.reposContributedToCoefficient * repos);
                
                // Display the computed prediction
                document.getElementById('computation').textContent = `Predicted Score: ${prediction.toFixed(2)}`;

                // Display the chart images
                const imageUrls = data.imageUrls;
                imageUrls.forEach(url => {
                    const img = document.createElement('img');
                    img.src = "http://localhost:8085" + url;
                    document.getElementById('imageContainer').appendChild(img);
                });
            })
            .catch(error => {
                console.error('Error:', error);
            });
    });
    </script>
</body>
</html>