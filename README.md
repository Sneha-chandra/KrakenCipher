<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Kraken's Cipher</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #0a192f;
            color: white;
            padding: 20px;
        }
        .container {
            max-width: 500px;
            margin: auto;
            background: #112240;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.2);
        }
        input {
            padding: 10px;
            width: 80%;
            margin: 10px 0;
            border-radius: 5px;
            border: none;
            text-align: center;
        }
        button {
            background: #64ffda;
            color: #112240;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background: #52d3b8;
        }
        #result {
            margin-top: 15px;
            font-size: 18px;
            font-weight: bold;
        }
    </style>
    <script>
         // Disable Right-Click, Inspect Element, View Source
         document.addEventListener("contextmenu", event => event.preventDefault());
        document.addEventListener("keydown", event => {
            if (event.key === "F12" || 
                (event.ctrlKey && event.shiftKey && event.key === "I") || 
                (event.ctrlKey && event.key === "U")) {
                event.preventDefault();
            }
        });
                

        function checkAnswer() {
    let answer = document.getElementById("guess").value.trim();
    let encodedCorrectAnswer = "S3Jha2Vuc19zZWNyZXQ="; // Base64 encoded version of "Krakens_secret"
    
    // Decrypting the Base64 encoded answer
    let decodedAnswer = atob(encodedCorrectAnswer); // Base64 decoding

    if (answer === decodedAnswer) {
        document.getElementById("result").innerHTML = 
            "✅ Congratulations! You found the treasure! <br><strong>FLAG{krakens_secret_IET}</strong>";
    } else {
        document.getElementById("result").innerHTML = "❌ Incorrect! Try again.";
    }
}


        function decryptKrakenCipher(cipherText) {
            return atob(cipherText);
            let b64_encoded = cipherText.split('').map(c => String.fromCharCode(c.charCodeAt(0) - 3)).join(''); // Reverse ASCII shift
            let reversed_text = atob(b64_encoded); // Base64 decode
            return reversed_text.split('').reverse().join(''); // Reverse back  
        }
    </script>
</head>
<body>
    <div class="container">
        <h1>The Kraken's Cipher</h1>
        <p>"The beast's code twists like the sea – only the brave can untangle it."</p>
        <input type="text" id="guess" placeholder="Enter the decrypted text">
        <button onclick="checkAnswer()">Submit</button>
        <p id="result"></p>
    </div>
</body>
</html>
