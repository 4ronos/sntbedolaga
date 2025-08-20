# 🤖 Remnawave Bedolaga Bot 2.0.0

## ⚠️ Важная пометка

Бедолага был **полностью** переписан с нуля. 

Версия 2.0.0 — Это не просто обновление, это в целом - переосмысление логики работы бота, с полностью новой архитектурой, улучшенной производительностью и расширенным функционалом. 

**Обновление не совместимо со крайней версией 1.4.2!** 

Поэтому заранее извинюсь перед всеми, кто уже начал пользоваться моим бедолагой, увы, делать нормальную миграцию всех данных у меня уже совсем сил ноль, да и не ожидал такого успеха, поэтому-то и решил полностью переписать бота, пока еще не совсем поздно, доработав его опираясь на ваши отзывы и запросы. 

На данный момент новая версия бота, по моим оценкам, отлажена на **90%**+-. 

Собственно, те кто установил бота - могут пока перенести всех юзеров из панели в бота через синхронизацию.

<div align="center">

[![Docker Image](https://img.shields.io/badge/Docker-fr1ngg/remnawave--bedolaga--telegram--bot-blue?logo=docker&logoColor=white)](https://hub.docker.com/r/fr1ngg/remnawave-bedolaga-telegram-bot)
[![Python](https://img.shields.io/badge/Python-3.11+-blue?logo=python&logoColor=white)](https://python.org)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15+-blue?logo=postgresql&logoColor=white)](https://postgresql.org)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Stars](https://img.shields.io/github/stars/Fr1ngg/remnawave-bedolaga-telegram-bot?style=social)](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/stargazers)

![Logo](./assets/logo2.svg)

**Современный Telegram-бот для управления VPN подписками через Remnawave API**

*Полнофункциональное решение с управлением пользователями, платежами и администрированием*

[🚀 Быстрый старт](#-быстрый-старт) • [📖 Документация](#-документация) • [💬 Поддержка](#-поддержка) • [🤝 Вклад](#-вклад-в-проект)

</div>

---

## ✨ Основные возможности

<table>
<tr>
<td width="50%">

### 👤 **Для пользователей**
- 💰 **Управление балансом** - Telegram Stars + Telegram Tribute
- 🛒 **Покупка подписки** - Гибкая конфигурация подписки
- 📱 **Управление подписками** - просмотр, продление, ссылки, настройка автопродления. Полня конфигурация своей подписки: выбор лимита трафика, выбор стран(Работает через сквады Remnawave), выбор кол-ва устройств. Возможность платно сбросить, увеличить кол-во трафика на подписке, изменить подключенные сервера(сквады) у подписки
- 🎁 **Промокоды** - денежные бонусы, дни подписки(На отладке) + триал подписка по коду(На отладке)
- 👥 **Реферальная программа** - зарабатывай с друзей и их последующих покупок
- 🆓 **Тестовая подписка** - бесплатная пробная версия
- 💬 **Уведомления об истечении подписки**
- 📖 **Правила сервиса**

</td>
<td width="50%">

### ⚙️ **Для администраторов**
- 📊 **Детальная статистика** - пользователи, подписки
- 👥 **Управление пользователями** - поиск, редактирование, баланс
- 🎫 **Управление промокодами** - создание, статистика, массовые операции
- 🖥 **Мониторинг системы** - состояние нод/панели, синхронизация с Remnawave, просмотр сквадов и их создание
- 📨 **Рассылки** - уведомления пользователям по критериям 
- 🔍 **Мониторинг подписок** - Включение/отключение мониторинга, просмотр настроек, лога, тестирование сервиса
- 📋 **Правила сервиса** - настройка через админ-панель
- 💰 **Рефералы** - статистика рефералов

</td>
</tr>
</table>

## Структура проекта

После установки в `/opt/bedolaga-bot/`:

```
bedolaga_bot/
├── main.py                    # Точка входа                
├── requirements.txt           # Зависимости                
├── .env.example               # Пример конфига               
│
├── app/
│   ├── __init__.py
│   ├── bot.py                 # Инициализация бота          
│   ├── config.py              # Конфигурация                 
│   ├── states.py              # FSM состояния                   
│   │
│   ├── handlers/              # Обработчики
│   │   ├── __init__.py
│   │   ├── start.py           # Регистрация и старт          
│   │   ├── menu.py            # Главное меню               
│   │   ├── subscription.py    # Подписки                   
│   │   ├── balance.py         # Баланс                   
│   │   ├── promocode.py       # Промокоды                  
│   │   ├── referral.py        # Рефералы                  
│   │   ├── support.py         # Техподдержка                  
│   │   ├── admin/             # Админ панель
│   │   │   ├── __init__.py
│   │   │   ├── main.py        # Главная админки           
│   │   │   ├── users.py       # Управление юзерами          
│   │   │   ├── subscriptions.py # Настройки подписок         
│   │   │   ├── promocodes.py  # Управление промокодами        
│   │   │   ├── messages.py    # Рассылки                      
│   │   │   ├── monitoring.py  # Мониторинг                  
│   │   │   ├── referrals.py   # Статистика рефералов          
│   │   │   ├── rules.py       # Правила сервиса  
│   │   │   ├── servers.py             
│   │   │   ├── remnawave.py   # Система RemnaWave            
│   │   │   └── statistics.py  # Общая статистика             
│   │   └── common.py          # Общие обработчики            
│   │
│   ├── keyboards/             # Клавиатуры
│   │   ├── __init__.py
│   │   ├── inline.py          # Inline клавиатуры          
│   │   ├── reply.py           # Reply клавиатуры         
│   │   └── admin.py           # Админские клавиатуры       
│   │
│   ├── database/              # База данных
│   │   ├── __init__.py
│   │   ├── models.py          # Модели SQLAlchemy            
│   │   ├── database.py        # Подключение к БД            
│   │   └── crud/              # CRUD операции
│   │       ├── __init__.py
│   │       ├── user.py                                      
│   │       ├── subscription.py                             
│   │       ├── transaction.py             
│   │       ├── rules.py      
│   │       ├── server_squad.py                       
│   │       ├── promocode.py                                
│   │       └── referral.py                                 
│   │
│   ├── services/              # Бизнес-логика
│   │   ├── __init__.py                                        
│   │   ├── user_service.py             # Сервис пользователей          
│   │   ├── subscription_service.py     # Сервис подписок          
│   │   ├── payment_service.py          # Платежи                      
│   │   ├── promocode_service.py        # Промокоды                    
│   │   ├── referral_service.py         # Рефералы                        
│   │   ├── monitoring_service.py       # Мониторинг     
│   │   ├── tribute_service.py               
│   │   └── remnawave_service.py       # Интеграция с RemnaWave       
│   │
│   ├── utils/                 # Утилиты
│   │   ├── __init__.py                                          
│   │   ├── decorators.py      # Декораторы                      
│   │   ├── formatters.py      # Форматирование данных            
│   │   ├── validators.py      # Валидация                       
│   │   ├── pagination.py      # Пагинация    
│   │   ├── user_utils.py                        
│   │   └── cache.py           # Кеширование                     
│   │
│   ├── middlewares/           # Middleware
│   │   ├── __init__.py
│   │   ├── auth.py           # Авторизация                  
│   │   ├── logging.py        # Логирование                   
│   │   └── throttling.py     # Ограничение запросов         
│   │
│   ├── localization/          # Локализация
│   │   ├── __init__.py
│   │   ├── texts.py          # Тексты интерфейса             
│   │   └── languages/
│   │
│   └── external/              # Внешние API
│       ├── __init__.py
│       ├── remnawave_api.py   # Ваш API файл               
│       ├── telegram_stars.py  # Telegram Stars             
│       └── tribute.py         # Tribute платежи             
│
├── migrations/                # Миграции БД
│   └── alembic/
│
└── logs/                      # Логи
```

---

<details>
<summary>⚙️ Env параметры</summary>

### 3. Конфигурация

Скопируйте `.env.example` в `.env` и заполните переменные согласно таблицам ниже:

#### 🤖 Основные настройки бота

| Переменная | Описание | Пример |
|------------|----------|---------|
| `BOT_TOKEN` | Токен Telegram бота | `1234567890:AABBCCddEEffGGhhIIjjKKllMM` |
| `ADMIN_IDS` | ID администраторов (через запятую) | `123456789,987654321` |
| `SUPPORT_USERNAME` | Username техподдержки | `@support_bot` |

#### 🗄️ База данных и кеширование

| Переменная | Описание | Пример |
|------------|----------|---------|
| `DATABASE_URL` | URL подключения к БД | `sqlite+aiosqlite:///./bot.db` |
| `REDIS_URL` | URL подключения к Redis | `redis://localhost:6379/0` |

#### 🖥️ Remnawave API

| Переменная | Описание | Пример |
|------------|----------|---------|
| `REMNAWAVE_API_URL` | URL API Remnawave | `https://panel.example.com` |
| `REMNAWAVE_API_KEY` | JWT токен для API | `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...` |

#### 🎁 Тестовая подписка

| Переменная | Описание | По умолчанию |
|------------|----------|--------------|
| `TRIAL_ENABLED` | Включить триал | `true` |
| `TRIAL_DURATION_DAYS` | Дней триала | `3` |
| `TRIAL_TRAFFIC_LIMIT_GB` | Лимит трафика (ГБ) | `10` |
| `TRIAL_DEVICE_LIMIT` | Лимит устройств | `2` |
| `TRIAL_SQUAD_UUID` | UUID сквада для триала | `b96250d4-1455-45b1-ab38-e617a8e8f5ff` |
| `TRIAL_NOTIFICATION_ENABLED` | Уведомления об истечении | `true` |
| `TRIAL_NOTIFICATION_HOURS_AFTER` | Через сколько часов уведомить | `1` |
| `TRIAL_WARNING_HOURS` | За сколько часов предупредить | `2` |

#### 💰 Ценообразование (в копейках)

| Переменная | Описание | По умолчанию |
|------------|----------|--------------|
| `BASE_SUBSCRIPTION_PRICE` | Базовая цена подписки | `50000` |
| `PRICE_14_DAYS` | 14 дней | `5000` |
| `PRICE_30_DAYS` | 30 дней | `9900` |
| `PRICE_60_DAYS` | 60 дней | `18900` |
| `PRICE_90_DAYS` | 90 дней | `26900` |
| `PRICE_180_DAYS` | 180 дней | `49900` |
| `PRICE_360_DAYS` | 360 дней | `89900` |
| `PRICE_TRAFFIC_5GB` | 5 ГБ трафика | `2000` |
| `PRICE_TRAFFIC_10GB` | 10 ГБ трафика | `4000` |
| `PRICE_TRAFFIC_25GB` | 25 ГБ трафика | `6000` |
| `PRICE_TRAFFIC_50GB` | 50 ГБ трафика | `10000` |
| `PRICE_TRAFFIC_100GB` | 100 ГБ трафика | `15000` |
| `PRICE_TRAFFIC_250GB` | 250 ГБ трафика | `20000` |
| `PRICE_TRAFFIC_UNLIMITED` | Безлимитный трафик | `25000` |
| `PRICE_PER_DEVICE` | Цена за дополнительное устройство | `5000` |
| `DEFAULT_TRAFFIC_RESET_STRATEGY` | Стратегия сброса трафика | `MONTH` |

#### 🤝 Реферальная система (В копейках)

| Переменная | Описание | По умолчанию |
|------------|----------|--------------|
| `REFERRAL_REGISTRATION_REWARD` | Награда за регистрацию реферала | `5000` |
| `REFERRED_USER_REWARD` | Бонус приглашенному пользователю | `2500` |
| `REFERRAL_COMMISSION_PERCENT` | % с покупок рефералов | `10` |

#### ⭐ Telegram Stars

| Переменная | Описание | Пример |
|------------|----------|---------|
| `TELEGRAM_STARS_ENABLED` | Включить оплату звездами | `true` |

#### 💳 Tribute

| Переменная | Описание | Пример |
|------------|----------|---------|
| `TRIBUTE_ENABLED` | Включить оплату через Tribute | `true` |
| `TRIBUTE_API_KEY` | API ключ Tribute | `d03424f0-8427c-1234-2134-a472439` |
| `TRIBUTE_DONATE_LINK` | Ссылка на донат | `https://t.me/tribute/app?startapp=XXXX` |
| `TRIBUTE_WEBHOOK_PATH` | Путь для webhook | `/tribute-webhook` |
| `TRIBUTE_WEBHOOK_PORT` | Порт для webhook | `8081` |
| `TRIBUTE_WEBHOOK_SECRET` | Секрет для webhook | `your_webhook_secret` |
| `WEBHOOK_URL` | URL для webhook | `https://your-domain.com` |
| `WEBHOOK_PATH` | Путь для webhook (не менять) | `/webhook` |

#### 🔍 Мониторинг и автоплатежи

| Переменная | Описание | По умолчанию |
|------------|----------|--------------|
| `MONITORING_INTERVAL` | Интервал мониторинга (сек) | `60` |
| `AUTOPAY_WARNING_DAYS` | Дни предупреждения о списании | `3,1` |
| `ENABLE_NOTIFICATIONS` | Включить уведомления | `true` |
| `NOTIFICATION_RETRY_ATTEMPTS` | Попытки отправки уведомлений | `3` |
| `MONITORING_LOGS_RETENTION_DAYS` | Хранение логов мониторинга (дни) | `30` |
| `INACTIVE_USER_DELETE_MONTHS` | Удаление неактивных пользователей (мес) | `3` |

#### 🌐 Локализация и прочее

| Переменная | Описание | По умолчанию |
|------------|----------|--------------|
| `DEFAULT_LANGUAGE` | Язык по умолчанию (Англа нет, но все для его реализации есть) | `ru` |
| `AVAILABLE_LANGUAGES` | Доступные языки | `ru,en` |
| `LOG_LEVEL` | Уровень логирования | `INFO` |
| `LOG_FILE` | Файл логов | `/tmp/bot.log` |
| `DEBUG` | Режим отладки | `false` |
</details>
<details>
<summary>⚙️ Настройка Telegram Tribute</summary>

1) Регистрируемся и проходим верификацию в Tribute
2) Создаем донат ссылку, копируем вставляем в .env бота, конфигурируем остальные параметры из .env.example для работы Tribute
3) Настраиваем обратное прокси на /tribute-webhook

3.1 Пример для докера Caddy 

    https://test.example.com {
        # Tribute webhook endpoint
        handle /tribute-webhook* {
            reverse_proxy localhost:8081 {
                header_up Host {host}
                header_up X-Real-IP {remote_host}
            }
        }
    
        # Health check для webhook сервиса
        handle /webhook-health {
            reverse_proxy localhost:8081/health {
                header_up Host {host}
                header_up X-Real-IP {remote_host}
            }
        }

3.2 Пример для докера с Nginx 

     server {
        listen 80;
        server_name yourdomain.com;

        location /tribute-webhook {
            proxy_pass http://127.0.0.1:8081;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        
            proxy_connect_timeout 60s;
            proxy_send_timeout 60s;
            proxy_read_timeout 60s;
        
            client_max_body_size 10M;
        }

        location /webhook-health {
            proxy_pass http://127.0.0.1:8081/health;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
    }

3.3 Рестартим Бота, рестратим Caddy/Nginx   

4) Указываем ссылку на наш хук в настройках Tribute: https://test.example.com/tribute-webhook, создаем API ключ вписываем в .env бота

5) Делаем тест - если успешно, значит все настроили правильно. Не успешный тест - проверяй доступность хука, где-то ты что-то не так настроил
   
6) Тестируем пополнение через бота


</details>

🐳 Docker Compose примеры

<details>
<summary>🏠 Для локальной установки (панель + бот)</summary>

Используя готовый образ:

```bash
docker run -d \
  --name vpn-bot \
  --env-file .env \
  -v $(pwd)/logs:/app/logs \
  fr1ngg/remnawave-bedolaga-telegram-bot:latest
```

```yaml
services:
  postgres:
    image: postgres:15-alpine
    container_name: remnawave_bot_db
    restart: unless-stopped
    environment:
      POSTGRES_DB: remnawave_bot
      POSTGRES_USER: remnawave_user
      POSTGRES_PASSWORD: secure_password_123
    volumes:
      - postgres_data:/var/lib/postgresql/data
    networks:
      - remnawave-network
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U remnawave_user -d remnawave_bot"]

  bot:
    image: fr1ngg/remnawave-bedolaga-telegram-bot:latest
    container_name: remnawave_bot
    restart: unless-stopped
    depends_on:
      postgres:
        condition: service_healthy
    env_file:
      - .env
    environment:
      DATABASE_URL: postgresql+asyncpg://remnawave_user:secure_password_123@postgres:5432/remnawave_bot
      REDIS_URL: redis://redis:6379/0
    volumes:
      - ./logs:/app/logs
      - ./data:/app/data
    ports:
      - "8081:8081"
    networks:
      - remnawave-network

volumes:
  postgres_data:

networks:
  bot_network:
    driver: bridge
    ipam:
      config:
        - subnet: 172.20.0.0/16
```

</details>

<details>
<summary>🌐 Для удаленной установки</summary>

```yaml
services:
  postgres:
    image: postgres:15-alpine
    container_name: remnawave_bot_db
    restart: unless-stopped
    environment:
      POSTGRES_DB: remnawave_bot
      POSTGRES_USER: remnawave_user
      POSTGRES_PASSWORD: secure_password_123
    volumes:
      - postgres_data:/var/lib/postgresql/data
    networks:
      - bot_network
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U remnawave_user -d remnawave_bot"]

  bot:
    image: fr1ngg/remnawave-bedolaga-telegram-bot:latest
    container_name: remnawave_bot
    restart: unless-stopped
    depends_on:
      postgres:
        condition: service_healthy
    env_file:
      - .env
    environment:
      DATABASE_URL: postgresql+asyncpg://remnawave_user:secure_password_123@postgres:5432/remnawave_bot
    volumes:
      - ./logs:/app/logs
      - ./data:/app/data
    ports:
      - "8081:8081"
    networks:
      - bot_network

  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    volumes:
      - redis_data:/data
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 30s
      timeout: 10s
      retries: 3
    networks:
      - bot_network

volumes:
  postgres_data:
  redis_data:

networks:
  bot_network:
    driver: bridge
    ipam:
      config:
        - subnet: 172.20.0.0/16
```

</details>

---

### 🔧 Первичная настройка в боте

После успешного запуска бота необходимо выполнить синхронизацию данных:

#### 📡 Синхронизация серверов (обязательно)

1. Зайдите в бот и откройте **Админ панель**
2. Перейдите в **Подписки** → **Управление серверами**
3. Нажмите **Синхронизация**
4. Дождитесь завершения процесса

> ⚠️ **Важно!** Без синхронизации серверов пользователи не смогут выбирать страны при покупке подписки. Сквады из вашей Remnawave панели автоматически импортируются в бота.

#### 👥 Синхронизация пользователей (если есть существующая база)

Если у вас уже были пользователи в Remnawave до установки бота:

1. Зайдите в **Админ панель** → **Remnawave**
2. Выберите **Синхронизация**
3. Нажмите **Синхронизировать всех**
4. Дождитесь завершения импорта пользователей и их подписок

> 💡 **Совет:** Синхронизация может занять несколько минут в зависимости от количества пользователей. Процесс отображается в режиме реального времени.

## 🎯 Использование

### 👤 Для пользователей

1. **Запуск** → Найдите бота и нажмите `/start`
2. **Правила** → Примите правила 
3. **Баланс** → "💰 Баланс" 
4. **Подписка** → "🛒 Купить подписку" → выбор тарифа → оплата
5. **Управление** → "📋 Мои подписки" → выбор → Конфигурация → получение ссылки
6. **Рефералы** → "👥 Рефералы" → поделиться ссылкой

### ⚙️ Для администраторов

Доступ через кнопку **"⚙️ Админ панель"**:

- **📦 Управление подписками** → создание и настройка серверов, цен
- **👥 Управление пользователями** → поиск, редактирование балансов, блокировка
- **🎁 Промокоды** → создание денежных бонусов, подарочных дней подписки 
- **📨 Рассылки** → уведомления пользователям по критериям 
- **🖥 Система Remnawave** → мониторинг нод/панели, синхронизация
- **📊 Статистика** → подробная аналитика

---

## 📊 Производительность

### 💪 Рекомендуемые ресурсы

| Пользователей | RAM | CPU | Диск | Описание |
|---------------|-----|-----|------|----------|
| **До 500** | 1GB | 1 vCPU | 10GB | Начальная конфигурация |
| **До 1,000** | 2GB | 1 vCPU | 20GB | Малый бизнес |
| **До 10,000** | 4GB | 2 vCPU | 50GB | Средний бизнес |
| **До 50,000** | 8GB | 4 vCPU | 100GB | Крупный бизнес |

### ⚡ Оптимизация

- **Redis** → включите для кэширования
- **PostgreSQL** → настройте для production нагрузок
- **Nginx** → используйте как reverse proxy 
- **Мониторинг** → отслеживайте через `

---

## 🔧 Управление

### 📋 Основные команды

```bash
# Переход в директорию
cd /opt/bedolaga-bot

# Управление через Docker Compose
docker compose up -d           # Запуск
docker compose down            # Остановка  
docker compose restart bot     # Перезапуск бота
docker compose logs -f bot     # Логи в реальном времени

# Управление через systemd (если настроено)
sudo systemctl start bedolaga-bot
sudo systemctl stop bedolaga-bot
sudo systemctl restart bedolaga-bot
```

### 🔄 Обновления

Для получения обновлений:

```bash
git pull origin main
pip install -r requirements.txt
alembic upgrade head
```

При использовании Docker:

```bash
docker pull fr1ngg/remnawave-bedolaga-telegram-bot:latest
docker-compose up -d
```
---

## 🐛 Устранение неполадок

### ❓ Частые проблемы

<details>
<summary>🤖 Бот не отвечает</summary>

**Проверьте:**
- ✅ Правильность `BOT_TOKEN`
- ✅ Интернет соединение
- ✅ Логи: `docker compose logs bot`

**Решение:**
```bash
# Перезапуск бота
docker compose restart bot

# Проверка токена
docker exec remnawave_bot env | grep BOT_TOKEN
```

</details>

<details>
<summary>🗄️ Ошибки базы данных</summary>

**Симптомы:**
- SQL ошибки в логах
- Бот не сохраняет данные

**Решение:**
```bash
# Проверка PostgreSQL
docker compose logs postgres
```

</details>

<details>
<summary>🔌 Проблемы с Remnawave API</summary>

**Проверьте:**
- ✅ Доступность `REMNAWAVE_URL`
- ✅ Валидность `REMNAWAVE_TOKEN`
- ✅ Сетевое подключение

**Диагностика:**
```bash
# Проверка URL
curl -I https://your-panel.com

# Тест API из контейнера
docker exec remnawave_bot curl -I http://remnawave:3000
```

</details>

---

## 🔒 Безопасность

- Все пароли и ключи хранятся в переменных окружения
- Валидация всех пользовательских данных
- Защита от SQL инъекций через SQLAlchemy ORM
- Middleware для авторизации и ограничения запросов
- Логирование всех важных операций

## 🗺️ Roadmap

### ✅ Реализовано
-----------------------------------------------------------------------------
---------------------------Версия 1.0.0-1.4.2--------------------------------
- ✅ **Мониторинг подписок** - автоуведомления и контроль
- ✅ **Telegram Stars** - пополнение баланса звездами  
- ✅ **Синхронизация Remnawave** - импорт пользователей и статистика
- ✅ **Реферальная система** - полнофункциональная программа
- ✅ **Игра удачи** - ежедневные розыгрыши бонусов (вырезано в версии 2.0)
- ✅ **Управление промокодами** - создание, редактирование, статистика
- ✅ **Правила сервиса** - настройка через админ-панель
- ✅ **Автоплатежи** - настраиваемое автопродление подписок
- ✅ **Просмотр подписок пользователей** - детальная статистика
- ✅ **Автоматическое пополнение лк с помощью доната Tribute**
-----------------------------------------------------------------------------
---------------------------Версия 2.0.0+-------------------------------------
- 🌟 Глобальное обновление 2.0 - полное обновление архитектуры, отказ от мультиподписок -> переход к единой конфигурируемой подписке

  
### 🎯 В планах

| Версия | Функция | Приоритет | Описание |
|--------|---------|-----------|----------|
| **v2.1.0** | Юкасса интеграция | 🔴 High | Автоматические платежи |
| **v2.2.0+** | Веб-панель управления | 🟡 Medium | Полный веб-интерфейс |
| **v2.3.0+** | Дополнительные платежи | 🟡 Medium | Сбербанк, Tinkoff, Crypto |
| **v2.3.0** | Уведомления | 🟡 Medium | Webhook, Email, другие чаты |

### 💡 Хотите добавить функцию?

- 🐛 [Сообщите о баге](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/issues)
- ✨ [Предложите улучшение](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/discussions)
- 🔧 [Создайте Pull Request](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/pulls)

---

## 🤝 Вклад в проект

### 💪 Как помочь

**🔧 Разработчикам:**
- Fork репозитория
- Создайте feature branch: `git checkout -b feature/amazing-feature`
- Внесите изменения и сделайте commit: `git commit -m 'Add amazing feature'`
- Push в branch: `git push origin feature/amazing-feature`
- Создайте Pull Request

**🐞 Пользователям:**
- Сообщайте о багах в [Issues](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/issues)
- Предлагайте идеи в [Discussions](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/discussions)
- Ставьте ⭐ проекту
- Рассказывайте друзьям

**💰 Спонсорам:**
- Поддержите разработку
- Закажите приоритетные функции
- Получите корпоративную поддержку

---

## 💬 Поддержка

### 📞 Контакты

- **Telegram:** [@fringg](https://t.me/fringg) - Писать исключительно по делу, я бы конечно был рад всем помочь настроить remnawave, ваши ноды, настроить вам бота, настроить вебхуки, но ребят я один и бота пилю тоже в соло, помощь вам занимает крайне много времени, поэтому если надумаете просить помочь что-то настроить, готовьтесь дарить мне шпагу подарком в тг)(
  
- **Issues:** [GitHub Issues](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/issues)
- **Discussions:** [GitHub Discussions](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/discussions)

### 📚 Полезные ссылки

- [📖 Документация Remnawave](https://docs.remna.st)
- [🤖 Создание Telegram бота](https://t.me/BotFather)
- [🐳 Docker документация](https://docs.docker.com)
- [🐘 PostgreSQL документация](https://www.postgresql.org/docs)

---

## 📄 Лицензия

Проект распространяется под лицензией **MIT**. Подробности в файле [LICENSE](LICENSE).

---

<div align="center">

## ⭐ История проекта

<div align="center">

![Stars](https://img.shields.io/github/stars/Fr1ngg/remnawave-bedolaga-telegram-bot?style=for-the-badge&logo=github&color=yellow)
![Forks](https://img.shields.io/github/forks/Fr1ngg/remnawave-bedolaga-telegram-bot?style=for-the-badge&logo=github&color=blue)
![Issues](https://img.shields.io/github/issues/Fr1ngg/remnawave-bedolaga-telegram-bot?style=for-the-badge&logo=github&color=red)
![Last Commit](https://img.shields.io/github/last-commit/Fr1ngg/remnawave-bedolaga-telegram-bot?style=for-the-badge&logo=github)

[![Star History Chart](https://api.star-history.com/svg?repos=Fr1ngg/remnawave-bedolaga-telegram-bot&type=Date)](https://star-history.com/#Fr1ngg/remnawave-bedolaga-telegram-bot&Date)

</div>

---

### 💝 Донатеры

Спасибо всем, кто поддерживает проект!

| Донатер | Сумма |
|---------|-------|
| 1) Илья (@ispanec_nn) | $15 |
| 2) @pilot_737800 | 1250 руб |
| 3) @Legacyyy777 | 600 руб |
| 4) @Legacyyy777 | 400 руб |

---

### Поддержать проект
[![Donate](https://img.shields.io/badge/Donate-Telegram-blue?style=for-the-badge)](https://t.me/tribute/app?startapp=duUO)

---

**💝 Создано с любовью для Remnawave сообщества**

*Автор не является профессиональным разработчиком, но прикладывает все усилия для создания удобного бота для ваших сервисов* 💪

*The English Readme is currently being written, with revisions for various payment systems and languages. If you have the opportunity, please help me with local optimization and translations. This would greatly help me in writing an open source project that is accessible to different markets/countries.*

[🔝 Вернуться наверх](#-remnawave-bedolaga-bot)

</div>
