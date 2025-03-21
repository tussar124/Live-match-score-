# Live-match-score-<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Live Match Score</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
        }
        .score-container {
            width: 50%;
            margin: auto;
            padding: 20px;
            background: white;
            box-shadow: 0px 0px 10px gray;
            border-radius: 10px;
            margin-top: 50px;
        }
        .match {
            font-size: 20px;
            font-weight: bold;
        }
        .score {
            font-size: 24px;
            color: red;
        }
    </style>
</head>
<body>

    <div class="score-container">
        <h2>Live Cricket Score</h2>
        <p class="match">New Zealand vs Pakistan</p>
        <p class="score" id="liveScore">Loading...</p>
    </div>

    <script>
        async function fetchLiveScore() {
            try {
                let response = await fetch('https://api.example.com/scores?matchId=56f52d9f-9fa7-44d1-a901-ce010df08564'); // Replace with the actual API endpoint
                let data = await response.json();
                document.getElementById("liveScore").innerText = `${data.match.team1} vs ${data.match.team2}: ${data.match.score}`;
            } catch (error) {
                document.getElementById("liveScore").innerText = "Failed to load score";
            }
        }

        setInterval(fetchLiveScore, 5000); // Update every 5 seconds
        fetchLiveScore();
    </script>

</body>
</html>
