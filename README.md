<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grade Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            margin: 0;
            padding: 20px;
        }
        .container {
            background-color: #fff;
            max-width: 500px;
            margin: 20px auto;
            padding: 20px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }
        input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background-color: #007BFF;
            color: #fff;
            border: none;
            padding: 10px 20px;
            cursor: pointer;
            border-radius: 5px;
            font-size: 16px;
        }
        button:hover {
            background-color: #0056b3;
        }
        .result {
            margin-top: 20px;
            padding: 10px;
            background-color: #e0f7fa;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Grade Calculator</h1>
        <p>Enter your prelim grade to calculate the required midterm and finals grade to pass.</p>

        <input type="number" id="prelimGrade" placeholder="Enter prelim grade (0-100)">
        <button onclick="calculateGrade()">Calculate</button>

        <div id="result" class="result"></div>
    </div>

    <script>
        function calculateGrade() {
            // Get the prelim grade from the input field
            let prelimGrade = parseFloat(document.getElementById('prelimGrade').value);
            
            // Check if the input is valid
            if (isNaN(prelimGrade) || prelimGrade < 0 || prelimGrade > 100) {
                document.getElementById('result').innerHTML = "Please enter a valid prelim grade between 0 and 100.";
                return;
            }

            // Calculate the prelim component (20% of the prelim grade)
            let prelimComponent = prelimGrade * 0.20;
            
            // Set the required overall grade to pass the subject (75%)
            let requiredOverallGrade = 75;
            
            // Calculate the remaining grade needed for midterms/finals
            let remainingGradeNeeded = requiredOverallGrade - prelimComponent;
            let requiredMidtermFinalsGrade = remainingGradeNeeded / 0.80;
            
            // Display the result
            if (requiredMidtermFinalsGrade <= 100) {
                document.getElementById('result').innerHTML = `With a prelim grade of ${prelimGrade}, you need a Midterm/Finals grade of ${requiredMidtermFinalsGrade.toFixed(2)}% to pass.`;
            } else {
                document.getElementById('result').innerHTML = `With a prelim grade of ${prelimGrade}, even a Midterm/Finals grade of 100% is not enough to pass.`;
            }
        }
    </script>
</body>
</html>
