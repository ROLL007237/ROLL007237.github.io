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
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }
        body {
            background: var(--tg-theme-bg-color, #ffffff);
            color: var(--tg-theme-text-color, #000000);
            padding-bottom: 60px;
        }
        .header {
            padding: 12px 16px;
            font-size: 20px;
            font-weight: 700;
            text-align: center;
            background: var(--tg-theme-bg-color, #ffffff);
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid var(--tg-theme-secondary-bg-color, #f0f0f0);
        }
        .tab-content {
            display: none;
            padding: 16px;
        }
        .tab-content.active {
            display: block;
        }
        /* Стиль списков (как в Telegram) */
        .list {
            background: var(--tg-theme-secondary-bg-color, #f9f9f9);
            border-radius: 12px;
            overflow: hidden;
            margin-bottom: 16px;
        }
        .list-item {
            padding: 12px 16px;
            border-bottom: 1px solid var(--tg-theme-secondary-bg-color, #f0f0f0);
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        .list-item:last-child {
            border-bottom: none;
        }
        /* Кнопки (Telegram-like) */
        .btn {
            background: var(--tg-theme-button-color, #0088cc);
            color: var(--tg-theme-button-text-color, #ffffff);
            border: none;
            border-radius: 10px;
            padding: 10px 16px;
            font-size: 16px;
            font-weight: 500;
            width: 100%;
            margin-top: 12px;
            cursor: pointer;
            text-align: center;
            display: block;
        }
        /* Нижнее меню (Tab Bar) */
        .tab-bar {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: var(--tg-theme-bg-color, #ffffff);
            display: flex;
            justify-content: space-around;
            padding: 10px 0;
            border-top: 1px solid var(--tg-theme-secondary-bg-color, #f0f0f0);
        }
        .tab-btn {
            display: flex;
            flex-direction: column;
            align-items: center;
            color: var(--tg-theme-text-color, #000);
            opacity: 0.6;
            font-size: 12px;
            cursor: pointer;
            background: none;
            border: none;
        }
        .tab-btn.active {
            opacity: 1;
            color: var(--tg-theme-button-color, #0088cc);
        }
        .tab-icon {
            font-size: 24px;
            margin-bottom: 4px;
        }
        /* Профиль */
        .profile {
            text-align: center;
            margin-top: 24px;
        }
        .profile-avatar {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            margin: 0 auto 12px;
            background: var(--tg-theme-button-color, #0088cc);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 32px;
            font-weight: bold;
        }
        /* Coming Soon */
        .coming-soon {
            text-align: center;
            padding: 40px 0;
            color: var(--tg-theme-hint-color, #999999);
        }
        .gift-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
        }
        .gift-card {
            background: var(--tg-theme-secondary-bg-color, #f9f9f9);
            border-radius: 12px;
            padding: 16px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="header">Mini App</div>

    <!-- Подарки -->
    <div id="gifts" class="tab-content active">
        <div class="list">
            <div class="list-item">
                <span>Ваши доступные подарки</span>
                <span>🎁</span>
            </div>
        </div>
        <div class="gift-grid">
            <div class="gift-card">Подарок 1</div>
            <div class="gift-card">Подарок 2</div>
            <div class="gift-card">Подарок 3</div>
            <div class="gift-card">Подарок 4</div>
        </div>
        <button class="btn">Получить подарок</button>
    </div>

    <!-- Маркет -->
    <div id="market" class="tab-content">
        <div class="coming-soon">
            <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExcW5pY3F5d2V5b2V4Z3F5eTZ5b2R5ZzR2eGJ6dW5qZzZ0eGZ1dSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o7aTskHEUdgCQAXde/giphy.gif" width="150">
            <h3>Маркет в разработке</h3>
            <p>Скоро здесь появятся крутые товары!</p>
        </div>
    </div>

    <!-- Таблица лидеров -->
    <div id="leaderboard" class="tab-content">
        <div class="list">
            <div class="list-item">
                <span>🏆 Топ игроков</span>
            </div>
            <div class="list-item">
                <span>1. Игрок 1</span>
                <span>1000 очков</span>
            </div>
            <div class="list-item">
                <span>2. Игрок 2</span>
                <span>800 очков</span>
            </div>
            <div class="list-item">
                <span>3. Игрок 3</span>
                <span>600 очков</span>
            </div>
        </div>
    </div>

    <!-- Профиль -->
    <div id="profile" class="tab-content">
        <div class="profile">
            <div class="profile-avatar" id="user-avatar">U</div>
            <h3 id="user-name">Пользователь</h3>
            <p>ID: <span id="user-id">123456789</span></p>
        </div>
        <div class="list" style="margin-top: 24px;">
            <div class="list-item">
                <span>Баланс</span>
                <span>500 монет</span>
            </div>
            <div class="list-item">
                <span>Уведомления</span>
                <span>🔔</span>
            </div>
        </div>
        <button class="btn" onclick="Telegram.WebApp.close()">Выйти</button>
    </div>

    <!-- Нижняя панель -->
    <div class="tab-bar">
        <button class="tab-btn active" onclick="openTab('gifts')">
            <span class="tab-icon">🎁</span>
            <span>Подарки</span>
        </button>
        <button class="tab-btn" onclick="openTab('market')">
            <span class="tab-icon">🛒</span>
            <span>Маркет</span>
        </button>
        <button class="tab-btn" onclick="openTab('leaderboard')">
            <span class="tab-icon">🏆</span>
            <span>Топ</span>
        </button>
        <button class="tab-btn" onclick="openTab('profile')">
            <span class="tab-icon">👤</span>
            <span>Профиль</span>
        </button>
    </div>

    <script>
        const tg = window.Telegram.WebApp;
        tg.expand(); // Развернуть на весь экран

        // Переключение вкладок
        function openTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(tab => tab.classList.remove('active'));
            document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));
            
            document.getElementById(tabId).classList.add('active');
            event.currentTarget.classList.add('active');
        }

        // Загрузка данных пользователя
        if (tg.initDataUnsafe.user) {
            const user = tg.initDataUnsafe.user;
            document.getElementById('user-avatar').textContent = user.first_name?.charAt(0) || 'U';
            document.getElementById('user-name').textContent = user.first_name || 'Пользователь';
            document.getElementById('user-id').textContent = user.id;
        }
    </script>
</body>
</html>
