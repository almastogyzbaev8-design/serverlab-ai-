# ServerLab AI — старт с нуля (Windows)

Автор сайта: **Ақшабаева Сымбат**.

## 1. Запуск на своём компьютере
1. Установи Node.js 20 или новее: https://nodejs.org/
2. Открой папку `serverlab_ai` в Visual Studio Code.
3. В меню выбери Terminal → New Terminal.
4. Выполни: `npm install`
5. Затем: `npm start`
6. Открой Chrome и зайди на http://127.0.0.1:4173

В режиме без `DATABASE_URL` сайт использует локальный файл `.localdata/serverlab-store.json`. Регистрация, вход и прогресс работают для демонстрации на этом компьютере. Не удаляй `.localdata`, если хочешь сохранить локальные тестовые аккаунты.

## 2. Создать администратора локально
1. Скопируй `.env.example` и назови копию `.env`. Поле `DATABASE_URL` оставь пустым для локальной демонстрации.
2. В `.env` установи личные значения `ADMIN_EMAIL` и `ADMIN_PASSWORD` (не менее 12 символов), `ADMIN_NAME=Ақшабаева Сымбат`.
3. Перезапусти `npm start` и войди с этими данными.
4. Не загружай `.env` в GitHub и не пересылай пароль.

## 3. Для общей публичной версии
Render Free Service не сохраняет локальные файлы после перезапуска/сна/деплоя. Чтобы ученики с разных устройств видели общие аккаунты и результаты, создай PostgreSQL на Render и укажи его **Internal Database URL** в `Environment → DATABASE_URL` сервиса. После redeploy открой `/api/status` и проверь `dbConnected:true` и `storageMode:"postgresql"`.

Команды Render: Build Command `npm install`; Start Command `npm start`; Root Directory пустой, если `index.html`, `server.js`, `package.json` лежат в корне репозитория.

## 4. Языки и ИИ
Переключатель KZ/RU/EN переводит основные элементы интерфейса офлайн. Полный перевод длинных уроков и генеративные ответы ИИ используют `OPENAI_API_KEY` в секретных переменных сервера; без ключа сайт продолжает работать в учебном/демо режиме.

## 5. Проверка
`npm run check` проверяет синтаксис JavaScript. `GET /api/status` показывает состояние БД и ИИ; `GET /healthz` проверяет сервер.
