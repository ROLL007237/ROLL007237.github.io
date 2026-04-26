<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Купцов Сергей — Backend Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #0a0a0f;
  --surface: #111118;
  --surface2: #18181f;
  --border: rgba(255,255,255,0.07);
  --border2: rgba(255,255,255,0.12);
  --accent: #e8ff47;
  --accent2: #47ffe8;
  --text: #f0f0f5;
  --muted: #7a7a90;
  --muted2: #4a4a60;
  --tag-bg: rgba(232,255,71,0.08);
  --tag-border: rgba(232,255,71,0.2);
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: 'JetBrains Mono', monospace;
  font-size: 14px;
  line-height: 1.7;
  min-height: 100vh;
  overflow-x: hidden;
}



.container {
  max-width: 900px;
  margin: 0 auto;
  padding: 0 2rem;
  position: relative;
  z-index: 1;
}

/* Header */
header {
  padding: 4rem 0 3rem;
  border-bottom: 1px solid var(--border);
  animation: fadeUp 0.6s ease both;
}

.header-inner {
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 2rem;
  align-items: start;
}

.avatar-wrap {
  position: relative;
}

.avatar-wrap img, .avatar-fallback {
  width: 96px;
  height: 96px;
  border-radius: 12px;
  border: 1px solid var(--border2);
  object-fit: cover;
}

.avatar-fallback {
  background: var(--surface2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Syne', sans-serif;
  font-size: 32px;
  font-weight: 700;
  color: var(--accent);
}

.status-dot {
  position: absolute;
  bottom: 6px;
  right: 6px;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: #4ade80;
  border: 2px solid var(--bg);
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%, 100% { box-shadow: 0 0 0 0 rgba(74,222,128,0.4); }
  50% { box-shadow: 0 0 0 6px rgba(74,222,128,0); }
}

.header-info {}

.name {
  font-family: 'Syne', sans-serif;
  font-size: clamp(28px, 5vw, 44px);
  font-weight: 800;
  line-height: 1.1;
  letter-spacing: -0.02em;
  margin-bottom: 0.4rem;
}

.name span { color: var(--accent); }

.role {
  font-family: 'Syne', sans-serif;
  font-size: 15px;
  font-weight: 500;
  color: var(--muted);
  letter-spacing: 0.1em;
  text-transform: uppercase;
  margin-bottom: 1rem;
}

.contact-row {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem 1.5rem;
  margin-bottom: 1rem;
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 13px;
  color: var(--muted);
  text-decoration: none;
  transition: color 0.2s;
}

.contact-item:hover { color: var(--accent); }

.contact-item svg { flex-shrink: 0; }

.badges {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-top: 0.75rem;
}

.badge {
  font-size: 11px;
  font-family: 'Syne', sans-serif;
  font-weight: 600;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  padding: 3px 10px;
  border-radius: 4px;
  border: 1px solid;
}

.badge-green { background: rgba(74,222,128,0.08); border-color: rgba(74,222,128,0.25); color: #4ade80; }
.badge-accent { background: var(--tag-bg); border-color: var(--tag-border); color: var(--accent); }
.badge-blue { background: rgba(71,255,232,0.08); border-color: rgba(71,255,232,0.2); color: var(--accent2); }

/* Main grid */
main {
  display: grid;
  grid-template-columns: 1fr 280px;
  gap: 3rem;
  padding: 3rem 0;
}

@media (max-width: 680px) {
  main { grid-template-columns: 1fr; gap: 2rem; }
  .header-inner { grid-template-columns: 1fr; }
}

/* Sections */
section { margin-bottom: 2.5rem; }

.section-label {
  font-family: 'Syne', sans-serif;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--accent);
  margin-bottom: 1.25rem;
  display: flex;
  align-items: center;
  gap: 10px;
}

.section-label::after {
  content: '';
  flex: 1;
  height: 1px;
  background: var(--border);
}

/* Experience */
.job {
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 1.25rem;
  margin-bottom: 1rem;
  background: var(--surface);
  transition: border-color 0.2s;
  animation: fadeUp 0.6s ease both;
}

.job:hover { border-color: var(--border2); }

.job-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 1rem;
  margin-bottom: 0.5rem;
  flex-wrap: wrap;
}

.job-company {
  font-family: 'Syne', sans-serif;
  font-size: 15px;
  font-weight: 700;
  color: var(--text);
}

.job-title {
  font-size: 13px;
  color: var(--accent2);
  margin-top: 2px;
}

.job-period {
  font-size: 12px;
  color: var(--muted);
  text-align: right;
  white-space: nowrap;
}

.job-list {
  list-style: none;
  margin-top: 0.75rem;
}

.job-list li {
  font-size: 13px;
  color: var(--muted);
  padding: 3px 0 3px 16px;
  position: relative;
  line-height: 1.6;
}

.job-list li::before {
  content: '›';
  position: absolute;
  left: 0;
  color: var(--accent);
}

/* Skills */
.skill-group { margin-bottom: 1.25rem; }

.skill-group-label {
  font-size: 11px;
  font-weight: 500;
  color: var(--muted);
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin-bottom: 6px;
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 5px;
}

.skill-tag {
  font-size: 12px;
  padding: 3px 9px;
  border-radius: 4px;
  background: var(--surface2);
  border: 1px solid var(--border);
  color: var(--text);
  transition: all 0.15s;
}

.skill-tag:hover {
  border-color: var(--accent);
  color: var(--accent);
}

.skill-tag.primary {
  background: var(--tag-bg);
  border-color: var(--tag-border);
  color: var(--accent);
}

/* Sidebar */
.sidebar {}

/* Stats */
.stats-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 8px;
  margin-bottom: 1rem;
}

.stat-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 0.875rem;
  text-align: center;
}

.stat-number {
  font-family: 'Syne', sans-serif;
  font-size: 22px;
  font-weight: 800;
  color: var(--accent);
  line-height: 1;
  margin-bottom: 4px;
}

.stat-label-text {
  font-size: 10px;
  color: var(--muted);
  text-transform: uppercase;
  letter-spacing: 0.06em;
}

/* Repos */
.repo-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 0.875rem;
  margin-bottom: 8px;
  cursor: pointer;
  text-decoration: none;
  display: block;
  transition: all 0.15s;
}

.repo-card:hover {
  border-color: var(--accent);
  transform: translateX(2px);
}

.repo-name {
  font-family: 'Syne', sans-serif;
  font-size: 13px;
  font-weight: 600;
  color: var(--accent);
  margin-bottom: 4px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.repo-desc {
  font-size: 11px;
  color: var(--muted);
  line-height: 1.5;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.repo-meta-row {
  display: flex;
  gap: 10px;
  margin-top: 6px;
}

.repo-meta-item {
  font-size: 11px;
  color: var(--muted2);
  display: flex;
  align-items: center;
  gap: 3px;
}

/* Langs */
.lang-bar-wrap { margin-bottom: 1.5rem; }

.lang-bar {
  display: flex;
  height: 6px;
  border-radius: 3px;
  overflow: hidden;
  margin-bottom: 8px;
  background: var(--surface2);
}

.lang-segment { height: 100%; transition: all 0.3s; }

.lang-legend {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.lang-item {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 11px;
  color: var(--muted);
}

.lang-dot {
  width: 8px;
  height: 8px;
  border-radius: 2px;
  flex-shrink: 0;
}

/* Education */
.edu-item {
  padding: 1rem;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 8px;
  margin-bottom: 8px;
}

.edu-name {
  font-family: 'Syne', sans-serif;
  font-size: 13px;
  font-weight: 600;
  color: var(--text);
  margin-bottom: 3px;
}

.edu-spec {
  font-size: 12px;
  color: var(--accent2);
  margin-bottom: 2px;
}

.edu-year {
  font-size: 11px;
  color: var(--muted);
}

/* Salary */
.salary-box {
  background: var(--tag-bg);
  border: 1px solid var(--tag-border);
  border-radius: 8px;
  padding: 1rem;
  text-align: center;
  margin-bottom: 1.5rem;
}

.salary-number {
  font-family: 'Syne', sans-serif;
  font-size: 22px;
  font-weight: 800;
  color: var(--accent);
}

.salary-label {
  font-size: 11px;
  color: var(--muted);
  margin-top: 2px;
  text-transform: uppercase;
  letter-spacing: 0.06em;
}

/* Languages */
.lang-skill {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 6px 0;
  border-bottom: 1px solid var(--border);
  font-size: 13px;
}

.lang-level { color: var(--accent); font-size: 11px; }

/* Footer */
footer {
  border-top: 1px solid var(--border);
  padding: 1.5rem 0;
  text-align: center;
  color: var(--muted2);
  font-size: 12px;
  position: relative;
  z-index: 1;
}

/* Animations */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(16px); }
  to { opacity: 1; transform: translateY(0); }
}

.job:nth-child(1) { animation-delay: 0.05s; }
.job:nth-child(2) { animation-delay: 0.1s; }
.job:nth-child(3) { animation-delay: 0.15s; }

/* Loading state */
.loading-text {
  color: var(--muted);
  font-size: 12px;
  font-style: italic;
}

.gh-link {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 0.75rem 1rem;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 8px;
  color: var(--text);
  text-decoration: none;
  font-size: 13px;
  margin-bottom: 1.5rem;
  transition: all 0.15s;
}

.gh-link:hover { border-color: var(--accent); color: var(--accent); }
</style>
</head>
<body>

<div class="container">
  <header>
    <div class="header-inner">
      <div class="avatar-wrap">
        <div class="avatar-fallback" id="avatar-wrap">КС</div>
        <div class="status-dot"></div>
      </div>
      <div class="header-info">
        <div class="name">Купцов <span>Сергей</span></div>
        <div class="role">Backend / Fullstack Developer</div>
        <div class="contact-row">
          <a class="contact-item" href="tel:+79050367040">
            <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 9.81a19.79 19.79 0 01-3.07-8.67A2 2 0 012 1h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L6.91 8.91a16 16 0 006.18 6.18l1.27-1.27a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 16.92z"/></svg>
            +7 (905) 036-70-40
          </a>
          <a class="contact-item" href="mailto:orange-ez@mail.ru">
            <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
            orange-ez@mail.ru
          </a>
          <span class="contact-item">
            <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>
            Казань → Москва
          </span>
          <a class="contact-item" href="https://github.com/ROLL007237" target="_blank">
            <svg width="13" height="13" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.477 2 12c0 4.418 2.865 8.166 6.839 9.489.5.092.682-.217.682-.482 0-.237-.009-.866-.013-1.7-2.782.604-3.369-1.34-3.369-1.34-.454-1.156-1.11-1.464-1.11-1.464-.908-.62.069-.608.069-.608 1.003.07 1.531 1.03 1.531 1.03.892 1.529 2.341 1.087 2.91.831.092-.646.35-1.086.636-1.336-2.22-.253-4.555-1.11-4.555-4.943 0-1.091.39-1.984 1.029-2.683-.103-.253-.446-1.27.098-2.647 0 0 .84-.269 2.75 1.025A9.578 9.578 0 0112 6.836c.85.004 1.705.115 2.504.337 1.909-1.294 2.747-1.025 2.747-1.025.546 1.377.203 2.394.1 2.647.64.699 1.028 1.592 1.028 2.683 0 3.842-2.339 4.687-4.566 4.935.359.309.678.919.678 1.852 0 1.336-.012 2.415-.012 2.741 0 .267.18.578.688.48C19.138 20.163 22 16.418 22 12c0-5.523-4.477-10-10-10z"/></svg>
            ROLL007237
          </a>
        </div>
        <div class="badges">
          <span class="badge badge-green">● Открыт к офферам</span>
          <span class="badge badge-accent">3+ года опыта</span>
          <span class="badge badge-blue">Удалённо / Офис</span>
        </div>
      </div>
    </div>
  </header>

  <main>
    <div class="left-col">

      <section>
        <div class="section-label">Опыт работы</div>

        <div class="job">
          <div class="job-header">
            <div>
              <div class="job-company">МЛайн</div>
              <div class="job-title">Fullstack-разработчик</div>
            </div>
            <div class="job-period">Май 2024 — наст. время<br><span style="color:var(--accent);font-size:11px;">~2 года</span></div>
          </div>
          <ul class="job-list">
            <li>Интеграция сторонних API (Telegram, ЮKassa, Google Maps) через aiohttp с fault-tolerance, retry-логикой и логированием</li>
            <li>Проектирование и оптимизация БД с SQLAlchemy ORM — ускорение ключевых запросов в 2–3× с помощью EXPLAIN ANALYZE</li>
            <li>Реализация денормализованных таблиц для сложных отчётов, обновляемых фоновыми задачами</li>
            <li>Контейнеризация через Docker / docker-compose, настройка Nginx (reverse proxy, балансировка), деплой на VPS/VDS</li>
            <li>Автоматизация деплоя bash-скриптами, унификация dev и prod окружений</li>
          </ul>
        </div>

        <div class="job">
          <div class="job-header">
            <div>
              <div class="job-company">Миррико, Группа Компаний</div>
              <div class="job-title">DevOps-инженер</div>
            </div>
            <div class="job-period">Июнь — Август 2025<br><span style="color:var(--muted);font-size:11px;">3 мес.</span></div>
          </div>
          <ul class="job-list">
            <li>Поддержка серверной инфраструктуры, настройка серверных ОС</li>
            <li>Настройка маршрутизации корпоративного VPN и подключение к локальной сети</li>
            <li>Техническая поддержка других отделов компании</li>
          </ul>
        </div>

        <div class="job">
          <div class="job-header">
            <div>
              <div class="job-company">Wildberries</div>
              <div class="job-title">Python-разработчик</div>
            </div>
            <div class="job-period">Янв 2023 — Ноябрь 2024<br><span style="color:var(--muted);font-size:11px;">1 г. 11 мес.</span></div>
          </div>
          <ul class="job-list">
            <li>Разработка и обслуживание серверной части приложения</li>
            <li>Разработка и поддержка клиентской части веб-приложения</li>
            <li>Разработка клиентского API и составление технической документации</li>
          </ul>
        </div>
      </section>

      <section>
        <div class="section-label">Технологии</div>

        <div class="skill-group">
          <div class="skill-group-label">Backend</div>
          <div class="skill-tags">
            <span class="skill-tag primary">Python</span>
            <span class="skill-tag primary">FastAPI</span>
            <span class="skill-tag primary">Django</span>
            <span class="skill-tag primary">Flask</span>
            <span class="skill-tag">Golang</span>
            <span class="skill-tag">Asyncio</span>
            <span class="skill-tag">aiohttp</span>
            <span class="skill-tag">REST API</span>
          </div>
        </div>

        <div class="skill-group">
          <div class="skill-group-label">Базы данных</div>
          <div class="skill-tags">
            <span class="skill-tag primary">PostgreSQL</span>
            <span class="skill-tag primary">Redis</span>
            <span class="skill-tag">MySQL</span>
            <span class="skill-tag">SQLAlchemy ORM</span>
            <span class="skill-tag">SQL</span>
          </div>
        </div>

        <div class="skill-group">
          <div class="skill-group-label">DevOps / Инфраструктура</div>
          <div class="skill-tags">
            <span class="skill-tag primary">Docker</span>
            <span class="skill-tag">docker-compose</span>
            <span class="skill-tag">Nginx</span>
            <span class="skill-tag">Linux</span>
            <span class="skill-tag">VPS/VDS</span>
            <span class="skill-tag">Bash</span>
            <span class="skill-tag">Git</span>
          </div>
        </div>

        <div class="skill-group">
          <div class="skill-group-label">Frontend / Другое</div>
          <div class="skill-tags">
            <span class="skill-tag">HTML</span>
            <span class="skill-tag">JSON API</span>
            <span class="skill-tag">HTTP</span>
            <span class="skill-tag">ООП</span>
            <span class="skill-tag">Паттерны проектирования</span>
            <span class="skill-tag">Agile</span>
          </div>
        </div>
      </section>

      <section>
        <div class="section-label">Образование</div>

        <div class="edu-item">
          <div class="edu-name">Казанский (Приволжский) федеральный университет</div>
          <div class="edu-spec">ИТИС — Разработчик программного обеспечения</div>
          <div class="edu-year">Неоконченное высшее · Ожидаемый год: 2027</div>
        </div>

        <div class="edu-item">
          <div class="edu-name">IT-Лицей при УлГТУ</div>
          <div class="edu-spec">Информационные технологии</div>
          <div class="edu-year">2023</div>
        </div>
      </section>

    </div>

    <aside class="sidebar">

      <div class="salary-box">
        <div class="salary-number">100 000 ₽</div>
        <div class="salary-label">Желаемая зарплата · на руки</div>
      </div>

      <section>
        <div class="section-label">GitHub</div>
        <a class="gh-link" href="https://github.com/ROLL007237" target="_blank">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.477 2 12c0 4.418 2.865 8.166 6.839 9.489.5.092.682-.217.682-.482 0-.237-.009-.866-.013-1.7-2.782.604-3.369-1.34-3.369-1.34-.454-1.156-1.11-1.464-1.11-1.464-.908-.62.069-.608.069-.608 1.003.07 1.531 1.03 1.531 1.03.892 1.529 2.341 1.087 2.91.831.092-.646.35-1.086.636-1.336-2.22-.253-4.555-1.11-4.555-4.943 0-1.091.39-1.984 1.029-2.683-.103-.253-.446-1.27.098-2.647 0 0 .84-.269 2.75 1.025A9.578 9.578 0 0112 6.836c.85.004 1.705.115 2.504.337 1.909-1.294 2.747-1.025 2.747-1.025.546 1.377.203 2.394.1 2.647.64.699 1.028 1.592 1.028 2.683 0 3.842-2.339 4.687-4.566 4.935.359.309.678.919.678 1.852 0 1.336-.012 2.415-.012 2.741 0 .267.18.578.688.48C19.138 20.163 22 16.418 22 12c0-5.523-4.477-10-10-10z"/></svg>
          ROLL007237
        </a>

        <div class="stats-grid" id="gh-stats">
          <div class="stat-card"><div class="stat-number" id="repos-count">—</div><div class="stat-label-text">Репозитории</div></div>
          <div class="stat-card"><div class="stat-number" id="stars-count">—</div><div class="stat-label-text">Звёзды</div></div>
          <div class="stat-card"><div class="stat-number" id="followers-count">—</div><div class="stat-label-text">Подписчики</div></div>
          <div class="stat-card"><div class="stat-number" id="following-count">—</div><div class="stat-label-text">Подписки</div></div>
        </div>
      </section>

      <section>
        <div class="section-label">Языки в репозиториях</div>
        <div class="lang-bar" id="lang-bar"></div>
        <div class="lang-legend" id="lang-legend"><span class="loading-text">Загрузка...</span></div>
      </section>

      <section>
        <div class="section-label">Топ репозитории</div>
        <div id="repos-list"><span class="loading-text">Загрузка...</span></div>
      </section>

      <section>
        <div class="section-label">Языки</div>
        <div class="lang-skill">
          <span>Русский</span>
          <span class="lang-level">Родной</span>
        </div>
        <div class="lang-skill">
          <span>Английский</span>
          <span class="lang-level">C1 — Продвинутый</span>
        </div>
      </section>

    </aside>
  </main>

  <footer>
    Купцов Сергей Андреевич · Backend Developer · Обновлено апрель 2026
  </footer>
</div>

<script>
const LANG_COLORS = {
  Python:'#3572A5', JavaScript:'#f1e05a', TypeScript:'#3178c6',
  Go:'#00ADD8', Rust:'#dea584', Shell:'#89e051', HTML:'#e34c26',
  CSS:'#563d7c', Java:'#b07219', 'C++':'#f34b7d', C:'#555',
  Dockerfile:'#384d54', Makefile:'#427819'
};

async function loadGitHub() {
  try {
    const [userRes, reposRes] = await Promise.all([
      fetch('https://api.github.com/users/ROLL007237'),
      fetch('https://api.github.com/users/ROLL007237/repos?sort=pushed&per_page=100')
    ]);
    const user = await userRes.json();
    const repos = await reposRes.json();

    if (!Array.isArray(repos)) return;

    // Avatar
    if (user.avatar_url) {
      const wrap = document.getElementById('avatar-wrap');
      const img = document.createElement('img');
      img.src = user.avatar_url;
      img.alt = 'Сергей Купцов';
      img.style.cssText = 'width:96px;height:96px;border-radius:12px;border:1px solid rgba(255,255,255,0.12);object-fit:cover;';
      wrap.replaceWith(img);
    }

    // Stats
    document.getElementById('repos-count').textContent = user.public_repos || repos.length;
    document.getElementById('followers-count').textContent = user.followers || 0;
    document.getElementById('following-count').textContent = user.following || 0;

    const totalStars = repos.reduce((s, r) => s + (r.stargazers_count || 0), 0);
    document.getElementById('stars-count').textContent = totalStars;

    // Languages
    const langCount = {};
    repos.forEach(r => { if (r.language) langCount[r.language] = (langCount[r.language]||0)+1; });
    const sorted = Object.entries(langCount).sort((a,b)=>b[1]-a[1]).slice(0,6);
    const total = sorted.reduce((s,[,c])=>s+c,0);

    const bar = document.getElementById('lang-bar');
    const legend = document.getElementById('lang-legend');
    bar.innerHTML = '';
    legend.innerHTML = '';

    sorted.forEach(([lang, count]) => {
      const pct = ((count/total)*100).toFixed(1);
      const color = LANG_COLORS[lang] || '#888';
      const seg = document.createElement('div');
      seg.className = 'lang-segment';
      seg.style.cssText = `width:${pct}%;background:${color};`;
      bar.appendChild(seg);

      legend.innerHTML += `<div class="lang-item"><div class="lang-dot" style="background:${color}"></div>${lang} <span style="color:var(--muted2)">${pct}%</span></div>`;
    });

    // Top repos
    const top = repos.filter(r=>!r.fork).sort((a,b)=>(b.stargazers_count+b.forks_count)-(a.stargazers_count+a.forks_count)).slice(0,5);
    const list = document.getElementById('repos-list');
    list.innerHTML = '';

    top.forEach(repo => {
      const color = LANG_COLORS[repo.language] || '#888';
      const a = document.createElement('a');
      a.href = repo.html_url;
      a.target = '_blank';
      a.className = 'repo-card';
      a.innerHTML = `
        <div class="repo-name">${repo.name}</div>
        ${repo.description ? `<div class="repo-desc">${repo.description}</div>` : ''}
        <div class="repo-meta-row">
          ${repo.language ? `<span class="repo-meta-item"><span style="width:8px;height:8px;border-radius:2px;background:${color};display:inline-block;margin-right:3px;"></span>${repo.language}</span>` : ''}
          ${repo.stargazers_count > 0 ? `<span class="repo-meta-item">★ ${repo.stargazers_count}</span>` : ''}
        </div>`;
      list.appendChild(a);
    });

    if (!top.length) list.innerHTML = '<span class="loading-text">Нет публичных репозиториев</span>';

  } catch(e) {
    console.error(e);
    document.getElementById('repos-list').innerHTML = '<span class="loading-text">Не удалось загрузить данные GitHub</span>';
  }
}

loadGitHub();
</script>
</body>
</html>
