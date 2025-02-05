<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Valentine's Yes Game</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background-color: pink;
            font-family: Arial, sans-serif;
            text-align: center;
            position: relative;
        }
        h1 {
            color: red;
        }
        .button-container {
            display: flex;
            gap: 20px;
            margin-top: 20px;
        }
        #yesButton {
            font-size: 24px;
            padding: 15px 30px;
            background-color: red;
            color: white;
            border: none;
            border-radius: 10px;
            cursor: not-allowed;
            transition: all 0.2s ease;
            opacity: 0.5;
            position: relative;
        }
        #noButton {
            font-size: 24px;
            padding: 15px 30px;
            background-color: gray;
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;
        }
        #hiddenMessage {
            display: none;
            font-size: 28px;
            color: red;
            font-weight: bold;
        }
        #packageDetails {
            display: none;
            margin-top: 20px;
            font-size: 18px;
            color: black;
        }
    </style>
</head>
<body>
    <h1>Will you be my Valentine?</h1>
    <div class="button-container">
        <button id="yesButton" disabled>Yes</button>
        <button id="noButton" onclick="handleNoClick()">No</button>
    </div>
    <p id="message"></p>
    <p id="hiddenMessage">YAY! ❤️ Happy Valentine's Day! ❤️</p>
    <div id="packageDetails">
        <p>💖 1500 - Whole day (terms and conditions apply)</p>
        <p>💕 1M - Holding hands</p>
        <p>💞 5M - Hugs</p>
        <p>💘 10.5M - Kiss</p>
        <p>🚗 20M or brand new Civic - Pag may balak ka pang iba</p>
        <p><br>Soooo paki PM nalang ako and please state sa PM kung anong package ang ia-avail and san mo ako idadate. 😘</p>
    </div>

    <script>
        let noClickCount = 0;
        let clickCount = 0;
        function handleNoClick() {
            let messages = ["Wag ganyan tayan 😢", "Sure na ba talaga?", "Pls pls pls 😭", "What if mag cry ako 😭"];
            if (noClickCount < messages.length) {
                document.getElementById("message").innerText = messages[noClickCount];
                noClickCount++;
            } else {
                document.getElementById("message").innerText = "Okay fine... you can now press Yes";
                let yesButton = document.getElementById("yesButton");
                yesButton.disabled = false;
                yesButton.style.cursor = "pointer";
                yesButton.style.opacity = "1";
                yesButton.onclick = shrinkButton;
            }
        }
        function shrinkButton() {
            clickCount++;
            let button = document.getElementById("yesButton");
            if (clickCount < 10) {
                let newSize = 24 - clickCount * 2;
                button.style.fontSize = newSize + "px";
                button.style.padding = (15 - clickCount) + "px " + (30 - clickCount * 2) + "px";
                moveButton();
            } else {
                button.style.display = "none";
                document.getElementById("hiddenMessage").style.display = "block";
                document.getElementById("packageDetails").style.display = "block";
            }
        }
        function moveButton() {
            let button = document.getElementById("yesButton");
            let x = Math.random() * (window.innerWidth - button.offsetWidth);
            let y = Math.random() * (window.innerHeight - button.offsetHeight);
            button.style.left = x + "px";
            button.style.top = y + "px";
        }
    </script>
</body>
</html>
