<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Telegram Mini App</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f2f5;
        }
        .container {
            text-align: center;
            padding: 20px;
            border-radius: 10px;
            background: white;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        button {
            background-color: #0088cc;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            margin-top: 20px;
        }
        button:hover {
            background-color: #0077bb;
        }
        #result {
            margin-top: 20px;
            font-size: 24px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Telegram Mini App</h1>
        <p>Нажмите кнопку, чтобы получить случайное число:</p>
        <button onclick="generateRandomNumber()">Сгенерировать</button>
        <div id="result"></div>
    </div>

    <script>
        // Инициализация Telegram WebApp
        const tg = window.Telegram.WebApp;
        tg.expand(); // Развернуть приложение на весь экран

        function generateRandomNumber() {
            const randomNum = Math.floor(Math.random() * 100) + 1;
            document.getElementById('result').textContent = randomNum;
            
            // Можно отправить данные обратно в бота, если нужно
            tg.sendData(JSON.stringify({ randomNumber: randomNum }));
        }
    </script>
</body>
</html>
