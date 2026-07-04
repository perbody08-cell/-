# 🤖 Telegram AI Bot — Business + Direct Mode

Бот с двумя режимами:
- **Business Mode** — отвечает от имени пользователя через Telegram Business
- **Direct Mode** — общение с ботом напрямую как с AI-ассистентом

## 🚀 Деплой на Render

### Шаг 1: GitHub
1. Загрузи этот код на GitHub
2. Создай новый репозиторий (публичный или приватный)

### Шаг 2: Render Dashboard
1. Иди на [dashboard.render.com](https://dashboard.render.com)
2. Нажми **"New +"** → **"Blueprint"**
3. Подключи свой GitHub репозиторий
4. Render автоматически прочитает `render.yaml`

### Шаг 3: Переменные окружения
После создания сервиса, перейди в **Environment** и добавь:

| Переменная | Значение |
|-----------|----------|
| `BOT_TOKEN` | Токен от [@BotFather](https://t.me/BotFather) |
| `ADMIN_IDS` | Твой Telegram ID |

`DATABASE_URL` создается автоматически из PostgreSQL.

### Шаг 4: Deploy
Нажми **"Manual Deploy"** → **"Deploy latest commit"**

Готово! Бот запущен.

## 🛠️ Локальный запуск

```bash
# 1. Клонировать
git clone <repo-url>
cd telegram_bot

# 2. Виртуальное окружение
python -m venv venv
source venv/bin/activate  # Linux/Mac
# venv\Scripts\activate  # Windows

# 3. Зависимости
pip install -r requirements.txt

# 4. Настройка
cp .env.example .env
# Отредактируй .env

# 5. БД (через Docker)
docker run -d \
  --name bot-postgres \
  -e POSTGRES_USER=botuser \
  -e POSTGRES_PASSWORD=botpass \
  -e POSTGRES_DB=botdb \
  -p 5432:5432 \
  postgres:15-alpine

# 6. Запуск
python main.py
```

## 📁 Структура

```
telegram_bot/
├── main.py              # Точка входа
├── settings.py          # Конфигурация
├── requirements.txt     # Зависимости
├── render.yaml          # Конфиг Render
├── database/            # Модели и CRUD
├── handlers/            # Обработчики
├── services/            # LLM, промпты
└── keyboards/           # Клавиатуры
```

## 🎯 Использование

### Direct Mode
1. Найди бота в Telegram
2. Напиши `/start`
3. Общайся напрямую

### Business Mode
1. Нужен Telegram Business
2. Настройки → Автоматизация чатов → Добавить бота
3. Введи @username бота

## ⚙️ Команды

| Команда | Описание |
|---------|----------|
| `/start` | Главное меню |
| `/settings` | Настройки |
| `/help` | Инструкция |
| `/admin` | Админ-панель |
