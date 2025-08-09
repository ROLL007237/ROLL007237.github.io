<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Telegram Mini App</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        body {
            background-color: var(--tg-theme-bg-color, #f0f2f5);
            color: var(--tg-theme-text-color, #000000);
        }
        .container {
            max-width: 100%;
            padding: 10px;
        }
        .tab-buttons {
            display: flex;
            justify-content: space-around;
            background: var(--tg-theme-secondary-bg-color, #f0f0f0);
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            padding: 10px;
            border-top: 1px solid #ddd;
        }
        .tab-button {
            padding: 8px 16px;
            border: none;
            background: none;
            cursor: pointer;
            color: var(--tg-theme-text-color, #000);
            font-weight: bold;
        }
        .tab-button.active {
            color: var(--tg-theme-button-color, #0088cc);
            border-bottom: 2px solid var(--tg-theme-button-color, #0088cc);
        }
        .tab-content {
            display: none;
            padding: 20px;
            margin-bottom: 60px;
        }
        .tab-content.active {
            display: block;
        }
        .coming-soon {
            text-align: center;
            margin-top: 20px;
            font-size: 18px;
            color: var(--tg-theme-hint-color, #888);
        }
        .gifts-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
        }
        .gift-item {
            background: var(--tg-theme-secondary-bg-color, #fff);
            border-radius: 10px;
            padding: 10px;
            text-align: center;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        .leaderboard {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        .leaderboard-item {
            background: var(--tg-theme-secondary-bg-color, #fff);
            border-radius: 10px;
            padding: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .profile-info {
            text-align: center;
            margin-top: 20px;
        }
        .profile-avatar {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            margin: 0 auto;
            background: var(--tg-theme-button-color, #0088cc);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Подарки -->
        <div id="gifts" class="tab-content active">
            <h2>🎁 Подарки</h2>
            <div class="gifts-grid">
                <div class="gift-item">Подарок 1</div>
                <div class="gift-item">Подарок 2</div>
                <div class="gift-item">Подарок 3</div>
                <div class="gift-item">Подарок 4</div>
            </div>
        </div>

        <!-- Маркет -->
        <div id="market" class="tab-content">
            <h2>🛒 Маркет</h2>
            <div class="coming-soon">
                <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExcW5pY3F5d2V5b2V4Z3F5eTZ5b2R5ZzR2eGJ6dW5qZzZ0eGZ1dSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o7aTskHEUdgCQAXde/giphy.gif" alt="Coming Soon" width="200">
                <p>Скоро открытие!</p>
            </div>
        </div>

        <!-- Таблица лидеров -->
        <div id="leaderboard" class="tab-content">
            <h2>🏆 Таблица лидеров</h2>
            <div class="leaderboard">
                <div class="leaderboard-item">
                    <span>1. Пользователь 1</span>
                    <span>1000 очков</span>
                </div>
                <div class="leaderboard-item">
                    <span>2. Пользователь 2</span>
                    <span>800 очков</span>
                </div>
                <div class="leaderboard-item">
                    <span>3. Пользователь 3</span>
                    <span>600 очков</span>
                </div>
            </div>
        </div>

        <!-- Профиль -->
        <div id="profile" class="tab-content">
            <h2>👤 Профиль</h2>
            <div class="profile-info">
                <div class="profile-avatar">TG</div>
                <h3>Имя пользователя</h3>
                <p>ID: 123456789</p>
                <p>Очков: 500</p>
            </div>
        </div>
    </div>

    <!-- Нижнее меню -->
    <div class="tab-buttons">
        <button class="tab-button active" onclick="openTab('gifts')">🎁</button>
        <button class="tab-button" onclick="openTab('market')">🛒</button>
        <button class="tab-button" onclick="openTab('leaderboard')">🏆</button>
        <button class="tab-button" onclick="openTab('profile')">👤</button>
    </div>

    <script>
        const tg = window.Telegram.WebApp;
        tg.expand(); // Развернуть на весь экран

        function openTab(tabId) {
            // Скрыть все вкладки
            document.querySelectorAll('.tab-content').forEach(tab => {
                tab.classList.remove('active');
            });

            // Убрать активность у всех кнопок
            document.querySelectorAll('.tab-button').forEach(button => {
                button.classList.remove('active');
            });

            // Показать выбранную вкладку
            document.getElementById(tabId).classList.add('active');

            // Активировать кнопку
            event.currentTarget.classList.add('active');
        }

        // Можно добавить загрузку данных пользователя из Telegram
        if (tg.initDataUnsafe.user) {
            const user = tg.initDataUnsafe.user;
            const profileAvatar = document.querySelector('.profile-avatar');
            const profileName = document.querySelector('.profile-info h3');
            const profileId = document.querySelector('.profile-info p:nth-of-type(1)');

            profileAvatar.textContent = user.first_name ? user.first_name.charAt(0) : 'TG';
            profileName.textContent = user.first_name || 'Пользователь';
            profileId.textContent = `ID: ${user.id}`;
        }
    </script>
</body>
</html>
