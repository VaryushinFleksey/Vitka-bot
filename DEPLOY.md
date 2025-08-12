# Инструкция по деплою бота

## Локальный запуск

1. Установите зависимости:
```bash
npm install
```

2. Создайте файл `.env`:
```bash
TELEGRAM_BOT_TOKEN=ваш_токен_бота
STORE_PATH=./store.json
OWNER_ID=ваш_telegram_id
```

3. Запустите бота:
```bash
npm start
```

## Деплой с Docker

### Вариант 1: Docker Compose

1. Создайте файл `.env` с переменными окружения
2. Запустите:
```bash
docker-compose up -d
```

### Вариант 2: Docker

1. Соберите образ:
```bash
docker build -t days-left-bot .
```

2. Запустите контейнер:
```bash
docker run -d \
  --name days-left-bot \
  -e TELEGRAM_BOT_TOKEN=ваш_токен_бота \
  -e OWNER_ID=ваш_telegram_id \
  -v $(pwd)/store.json:/app/store.json \
  days-left-bot
```

## Деплой на хостинге

### Railway
1. Подключите репозиторий к Railway
2. Установите переменные окружения в настройках проекта:
   - `TELEGRAM_BOT_TOKEN`
   - `OWNER_ID`

### Heroku
1. Создайте приложение на Heroku
2. Подключите репозиторий
3. Установите переменные окружения:
```bash
heroku config:set TELEGRAM_BOT_TOKEN=ваш_токен_бота
heroku config:set OWNER_ID=ваш_telegram_id
```

### VPS/Сервер
1. Склонируйте репозиторий
2. Создайте `.env` файл
3. Запустите с PM2:
```bash
npm install -g pm2
pm2 start index.js --name "days-left-bot"
pm2 startup
pm2 save
```

## Проверка работы

После деплоя отправьте боту команду `/start` для проверки.
