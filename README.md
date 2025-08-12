# 🤖 Remnawave Telegram Bot

[![Docker Image](https://img.shields.io/badge/Docker-fr1ngg/remnawave--bedolaga--telegram--bot-blue?logo=docker)](https://hub.docker.com/r/fr1ngg/remnawave-bedolaga-telegram-bot)
[![Python](https://img.shields.io/badge/Python-3.11+-blue?logo=python)](https://python.org)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15+-blue?logo=postgresql)](https://postgresql.org)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

![Remnawave Bedolaga Bot Logo](./assets/logo2.svg)

Современный Telegram бот для управления VPN подписками через Remnawave API с полным функционалом управления пользователями, платежами и администрированием.

## 🚀 Особенности

### 👤 Для пользователей
- 💰 **Управление балансом** - Пополнение через Telegram Stars + пополнение через поддержку p2p
- 🛒 **Покупка подписок** - различные тарифные планы c возможностью индивидуальной настройки сквада у плана
- 📱 **Управление подписками** - просмотр, продление, получение ссылок
- 🎁 **Система промокодов** - денежные коды
- 👥 **Реферальная программа** - зарабатывай с друзей
- 🎰 **Игра удачи** - выигрывай бонусы каждые 24 часа
- 🆓 **Тестовая подписка** - бесплатная пробная версия с детальной конфигурацией
- 🌐 **Мультиязычность** - русский и английский
- 📋 **Правила сервиса**
- ♾️ **Автопродление** - С настройкой вкл/выкл и кол-вом дней до автопродления.

### ⚙️ Для администраторов
- 📊 **Полная статистика** - пользователи, платежи, подписки
- 👥 **Управление пользователями** - поиск, редактирование, баланс
- 💳 **Управление платежами** - одобрение, отклонение, история
- 🎫 **Управление промокодами** - создание, редактирование, статистика
- ✍️ **Просмотр подписок юзеров**
- 🖥 **Мониторинг системы** - состояние нод, пользователей Remnawave
- 🔄 **Синхронизация данных** - импорт из Remnawave
- 📨 **Рассылки** - уведомления пользователям
- 🔍 **Мониторинг подписок** - автоматические уведомления об истечении и зачистка подписок с истекщим сроком для триал и обычных подписок
- 📋 **Правила сервиса** - Настройка страниц из админ панели
- ♾️ **Автопродление** - Статус сервиса, статистика автопродления, принудительное продление

## 📋 Требования

### Системные требования
- Docker и Docker Compose
- 1+ GB RAM
- 10+ GB свободного места

### Внешние сервисы
- **Telegram Bot Token** - создайте бота через [@BotFather](https://t.me/BotFather)
- **Remnawave API** - доступ к панели Remnawave
- **PostgreSQL** - автоматически разворачивается через Docker

## 🛠 Установка и запуск

### 1. Клонирование репозитория

```bash
git clone https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot.git
cd remnawave-bedolaga-telegram-bot
```

### 2. Настройка переменных окружения

Создайте файл `.env` на основе примера:

```bash
cp .env.example .env
nano .env
```

### 3. Конфигурация

#### 📋 Основные настройки

| Переменная | Описание | Пример |
|------------|----------|---------|
| `BOT_TOKEN` | Токен Telegram бота | `123456:ABC-DEF1234ghIkl-zyx` |
| `BOT_USERNAME` | Username бота (без @) | `your_bot_username` |
| `REMNAWAVE_URL` | URL панели Remnawave | `https://panel.example.com` |
| `REMNAWAVE_MODE` | Тип подключения | `remote/local` |
| `REMNAWAVE_TOKEN` | API токен Remnawave | `your_api_token` |
| `ADMIN_IDS` | ID администраторов (через запятую) | `123456789,987654321` |

#### 🎁 Реферальная программа

| Переменная | Описание | По умолчанию |
|------------|----------|--------------|
| `REFERRAL_FIRST_REWARD` | Награда за первого реферала | `100.0` |
| `REFERRAL_REFERRED_BONUS` | Бонус приглашенному | `100.0` |
| `REFERRAL_THRESHOLD` | Порог активации (руб.) | `200.0` |
| `REFERRAL_PERCENTAGE` | Процент со второго и послед. платежей | `0.2` (20%) |

#### 🎰 Игра удачи

| Переменная | Описание | По умолчанию |
|------------|----------|--------------|
| `LUCKY_GAME_ENABLED` | Включить игру | `true` |
| `LUCKY_GAME_REWARD` | Награда за выигрыш | `50.0` |
| `LUCKY_GAME_NUMBERS` | Всего чисел | `30` |
| `LUCKY_GAME_WINNING_COUNT` | Выигрышных чисел | `3` |

#### 🆓 Тестовая подписка

| Переменная | Описание | По умолчанию |
|------------|----------|--------------|
| `TRIAL_ENABLED` | Включить тестовую подписку | `true/false` |
| `TRIAL_DURATION_DAYS` | Длительность (дни) | `3` |
| `TRIAL_TRAFFIC_GB` | Лимит трафика (ГБ) | `2` |
| `TRIAL_SQUAD_UUID` | UUID squad для тестовых | `uuid-here` |

#### 🌟 Оплата за звезды

| Переменная | Описание | По умолчанию |
|------------|----------|--------------|
| `STARS_ENABLED=true` | Включить пополнение баланса за звезды | `true/false` |
| `STARS_100_RATE` | Курс за 100 звезд | `100` |
| `STARS_150_RATE` | Курс за 150 звезд | `150` |
| `STARS_250_RATE` | Курс за 250 звезд | `250` |
| `И тд` | Курс за XXX звезд | `XXXX` |


#### 💬 Сервис мониторинга сообщений

| Переменная | Описание | По умолчанию |
|------------|----------|--------------|
| `MONITOR_ENABLED` | Включить сервис подписку | `true/false` |
| `MONITOR_CHECK_INTERVAL` | Интервал проверки в секундах (1800 = 30 минут) (будет срабатывать через этот промежуток автоматически и слать уведомления) | `1800` |
| `MONITOR_DAILY_CHECK_HOUR` | Час ежедневной проверки (0-23, по умолчанию 10:00) | `10` |
| `DELETE_EXPIRED_TRIAL_DAYS` | Через сколько дней после истечения удалять триал подписки | `1` |
| `DELETE_EXPIRED_REGULAR_DAYS=7` | Через сколько дней после истечения удалять обычняе подписки | `7` |
| `MONITOR_WARNING_DAYS` | За сколько дней предупреждать (по умолчанию 3) | `3` |
| `AUTO_DELETE_ENABLED` | Включить автоматическое удаление при ежедневной проверке(true/false) | `true` |

### Максимально быстрый старт через скрипт управления ботом 
#### 🚀 Быстрая установка Remnawave Bedolaga Bot
<img width="419" height="348" alt="Снимок экрана 2025-08-12 в 01 24 57" src="https://github.com/user-attachments/assets/9ab876f5-2758-4c52-93dd-6c9c654a07aa" />


Автоматический установщик для Ubuntu сервера с полным управлением через интерактивное меню.

##### 📋 Требования

- **Ubuntu 18.04+** (рекомендуется Ubuntu 20.04 или 22.04)
- **Root доступ** или sudo права
- **Интернет соединение** для загрузки Docker образов

##### ⚡ Установка одной командой

###### Способ 1: Скачать и запустить
```bash
wget https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/raw/main/bedolaga.sh
chmod +x bedolaga.sh
sudo ./bedolaga.sh
```

###### Способ 2: Прямой запуск
```bash
curl -sSL https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/raw/main/bedolaga.sh | sudo bash
```

###### Способ 3: Клонирование репозитория
```bash
git clone https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot.git
cd remnawave-bedolaga-telegram-bot
sudo ./bedolaga.sh
```

#### 🔧 Что делает установщик

1. **Обновляет систему Ubuntu**
2. **Устанавливает Docker** и необходимые зависимости
3. **Создает структуру проекта** в `/opt/bedolaga-bot`
4. **Настраивает Docker Compose** (минимальная или расширенная конфигурация)
5. **Интерактивно настраивает .env файл** с параметрами бота
6. **Создает systemd службу** (опционально)
7. **Запускает интерактивное меню управления**

#### 📱 Интерактивное меню управления

После установки вы получите удобное меню для управления ботом:

##### Когда бот запущен:
- 🛑 Выключить бот
- 🔄 Перезапустить бот  
- 📺 Посмотреть логи в реальном времени
- ⬆️ Обновить бот
- 📋 Посмотреть логи
- 💾 Создать резервную копию БД
- ♻️ Восстановить базу данных
- ✏️ Редактировать .env файл
- 🩺 Диагностика базы данных
- Восстановление бд после обновления 1.3.3 -> 1.3.4
- 🗑️ Удалить базу данных
- ❌ Полностью удалить бота

##### Когда бот остановлен:
- ▶️ Запустить бот
- ⬆️ Обновить бот
- 📋 Посмотреть логи
- 💾 Создать резервную копию БД
- ♻️ Восстановить базу данных
- ✏️ Редактировать .env файл
- 🩺 Диагностика базы данных
- Восстановление бд после обновления 1.3.3 -> 1.3.4
- 🗑️ Удалить базы данных
- ❌ Полностью удалить бота

#### 🔧 Ручное управление через командную строку

```bash
# Перейти в папку проекта
cd /opt/bedolaga-bot

# Управление через Docker Compose
docker compose up -d          # Запустить
docker compose down           # Остановить
docker compose restart        # Перезапустить
docker compose logs -f bot    # Логи в реальном времени

# Управление через systemd (если служба создана)
sudo systemctl start bedolaga-bot
sudo systemctl stop bedolaga-bot
sudo systemctl restart bedolaga-bot
sudo systemctl status bedolaga-bot
```

#### 📂 Структура установки

```
/opt/bedolaga-bot/
├── docker-compose.yml    # Конфигурация контейнеров
├── .env                  # Настройки бота
├── logs/                 # Логи бота
├── data/                 # Данные бота
└── backup_*.sql          # Резервные копии БД
```

#### 🔄 Повторный запуск установщика

Если бот уже установлен, скрипт автоматически перейдет в режим управления без переустановки:

```bash
sudo ./bedolaga.sh
```

#### ❓ Решение проблем

### Бот не запускается
1. Проверьте логи: `docker compose logs bot`
2. Используйте диагностику в меню установщика
3. Убедитесь что все параметры в `.env` корректны

##### Проблемы с базой данных
1. Запустите диагностику базы данных из меню
2. Проверьте логи PostgreSQL: `docker compose logs postgres`
3. При необходимости создайте новую базу (удалите старую через меню)

##### Проблемы с Docker
```bash
# Перезапуск Docker
sudo systemctl restart docker

# Очистка неиспользуемых ресурсов
docker system prune -f
```

#### 📝 Дополнительные команды

```bash
# Обновление только бота (без остановки БД)
docker compose pull bot && docker compose up -d bot

# Резервная копия БД вручную
docker compose exec postgres pg_dump -U remnawave_user -d remnawave_bot > backup.sql

# Просмотр использования ресурсов
docker stats

# Просмотр всех volumes
docker volume ls
```

### 4. Docker Compose конфигурация

#### 🚀 Минимальная конфигурация (рекомендуется)

Создайте файл `docker-compose.yml` для базового запуска:

```yaml
services:
  # PostgreSQL Database
  postgres:
    image: postgres:15-alpine
    container_name: remnawave_bot_db
    restart: unless-stopped
    environment:
      POSTGRES_DB: remnawave_bot
      POSTGRES_USER: remnawave_user
      POSTGRES_PASSWORD: secure_password_123
      POSTGRES_INITDB_ARGS: "--encoding=UTF-8 --lc-collate=C --lc-ctype=C"
    volumes:
      - postgres_data:/var/lib/postgresql/data
    networks:
      - bot_network
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U remnawave_user -d remnawave_bot"]
      interval: 15s
      timeout: 10s
      retries: 5
      start_period: 30s

  # Remnawave Bot
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
    networks:
      - bot_network
    healthcheck:
      test: ["CMD-SHELL", "python -c 'print(\"Bot is running\")'"]
      interval: 30s
      timeout: 10s
      retries: 3
      start_period: 30s

volumes:
  postgres_data:
    driver: local

networks:
  bot_network:
    driver: bridge
```

#### ⚡ Полная конфигурация (с дополнительными сервисами)

Для расширенной настройки с Redis и Nginx создайте `docker-compose.full.yml`:

```yaml
services:
  # PostgreSQL Database
  postgres:
    image: postgres:15-alpine
    container_name: remnawave_bot_db
    restart: unless-stopped
    environment:
      POSTGRES_DB: remnawave_bot
      POSTGRES_USER: remnawave_user
      POSTGRES_PASSWORD: secure_password_123
      POSTGRES_INITDB_ARGS: "--encoding=UTF-8 --lc-collate=C --lc-ctype=C"
    volumes:
      - postgres_data:/var/lib/postgresql/data
    ports:
      - "5432:5432"
    networks:
      - bot_network
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U remnawave_user -d remnawave_bot"]
      interval: 15s
      timeout: 10s
      retries: 5
      start_period: 30s

  # Remnawave Bot
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
    networks:
      - bot_network
    healthcheck:
      test: ["CMD-SHELL", "python -c 'print(\"Bot is running\")'"]
      interval: 30s
      timeout: 10s
      retries: 3
      start_period: 30s

  # Redis (для кэширования и улучшения производительности)
  redis:
    image: redis:7-alpine
    container_name: remnawave_bot_redis
    restart: unless-stopped
    command: redis-server --appendonly yes --requirepass redis_password_123
    volumes:
      - redis_data:/data
    ports:
      - "6379:6379"
    networks:
      - bot_network
    healthcheck:
      test: ["CMD", "redis-cli", "--raw", "incr", "ping"]
      interval: 10s
      timeout: 3s
      retries: 5
    profiles:
      - with-redis

  # Nginx (для статических файлов или веб-интерфейса)
  nginx:
    image: nginx:alpine
    container_name: remnawave_bot_nginx
    restart: unless-stopped
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf:ro
      - ./ssl:/etc/nginx/ssl:ro
      - ./static:/usr/share/nginx/html:ro
    networks:
      - bot_network
    depends_on:
      - bot
    profiles:
      - with-nginx

volumes:
  postgres_data:
    driver: local
  redis_data:
    driver: local

networks:
  bot_network:
    driver: bridge
    ipam:
      config:
        - subnet: 172.20.0.0/16
```

### 5. Варианты запуска

#### 🚀 Быстрый старт (минимальная конфигурация)

```bash
# Запуск только бота и базы данных
docker-compose up -d

# Просмотр логов
docker-compose logs -f bot
```

#### ⚡ Расширенный запуск

```bash
# Запуск с Redis для улучшения производительности
docker-compose --profile with-redis up -d

# Запуск с Nginx для веб-интерфейса
docker-compose --profile with-nginx up -d

# Запуск со всеми сервисами
docker-compose --profile with-redis --profile with-nginx up -d

# Или используйте полную конфигурацию
docker-compose -f docker-compose.full.yml up -d
```

#### 🛑 Управление сервисами

```bash
# Остановка всех сервисов
docker-compose down

# Остановка с удалением volumes (ВНИМАНИЕ: удалит все данные!)
docker-compose down -v

# Перезапуск конкретного сервиса
docker-compose restart bot

# Просмотр статуса
docker-compose ps
```

#### 📋 Варианты конфигураций

| Конфигурация | Команда | Описание |
|--------------|---------|----------|
| **Минимальная** | `docker-compose up -d` | Только бот + PostgreSQL |
| **С Redis** | `docker-compose --profile with-redis up -d` | + кэширование |
| **С Nginx** | `docker-compose --profile with-nginx up -d` | + веб-сервер |
| **Полная** | `docker-compose --profile with-redis --profile with-nginx up -d` | Все сервисы |

## 📊 Мониторинг и управление

### Просмотр логов

```bash
# Логи бота
docker-compose logs -f bot

# Логи базы данных
docker-compose logs -f postgres

# Все логи
docker-compose logs -f
```

### Проверка состояния

```bash
# Статус контейнеров
docker-compose ps

# Использование ресурсов
docker stats
```

### Backup базы данных

```bash
# Создание backup
docker exec remnawave_bot_db pg_dump -U remnawave_user remnawave_bot > backup.sql

# Восстановление
docker exec -i remnawave_bot_db psql -U remnawave_user remnawave_bot < backup.sql
```

## 🔧 Обновление

### Обновление Docker образа

```bash
# Остановить сервисы
docker-compose down

# Обновить образ
docker-compose pull bot

# Запустить снова
docker-compose up -d

# Проверить логи
docker-compose logs -f bot
```

### Ручная сборка образа

```bash
# Клонировать репозиторий
git clone https://github.com/your-repo/remnawave-telegram-bot.git
cd remnawave-telegram-bot

# Собрать образ
docker build -t remnawave-bot .

# Изменить docker-compose.yml
# bot:
#   image: remnawave-bot  # вместо fr1ngg/remnawave-bedolaga-telegram-bot
```

## 🎯 Использование

### Для пользователей

1. **Запуск бота** - найдите бота по username и нажмите `/start`
2. **Выбор языка** - выберите русский или английский
3. **Пополнение баланса** - через меню "💰 Баланс" → "💳 Пополнить"
4. **Покупка подписки** - "🛒 Купить подписку" → выбор тарифа → оплата
5. **Управление подписками** - "📋 Мои подписки" → выбор подписки
6. **Реферальная программа** - "👥 Рефералы" → поделиться ссылкой

### Для администраторов

Администратор видит дополнительную кнопку "⚙️ Админ панель" с возможностями:

- **📦 Управление подписками** - создание тарифов
- **👥 Управление пользователями** - поиск, редактирование
- **💰 Управление балансом** - пополнение балансов
- **🎁 Управление промокодами** - создание скидок
- **📨 Рассылки** - отправка сообщений
- **🖥 Система Remnawave** - мониторинг нод и синхронизация

## 🔒 Безопасность

### Рекомендации

- ✅ Измените пароли PostgreSQL в `docker-compose.yml`
- ✅ Используйте HTTPS для Remnawave API
- ✅ Регулярно создавайте backup базы данных
- ✅ Ограничьте доступ к серверу через firewall

### Переменные безопасности

```bash
# Генерация безопасных паролей
openssl rand -base64 32  # для PostgreSQL
openssl rand -hex 16     # для Redis
```

## 🐛 Устранение неполадок

### Частые проблемы

| Проблема | Решение |
|----------|---------|
| Бот не отвечает | Проверьте `BOT_TOKEN` и интернет |
| Ошибка подключения к БД | Проверьте статус PostgreSQL контейнера |
| Ошибки Remnawave API | Проверьте `REMNAWAVE_URL` и `REMNAWAVE_TOKEN` |
| Игра удачи не работает | Проверьте `LUCKY_GAME_ENABLED=true` |

### Диагностика

```bash
# Проверка переменных окружения
docker exec remnawave_bot env | grep BOT_

# Подключение к базе данных
docker exec -it remnawave_bot_db psql -U remnawave_user remnawave_bot

# Перезапуск бота
docker-compose restart bot
```

### Логи и отладка

```bash
# Детальные логи
docker-compose logs -f --tail 100 bot

# Ошибки базы данных
docker-compose logs postgres | grep ERROR

# Проверка health checks
docker-compose ps
```

## 📈 Производительность

### Рекомендуемые ресурсы

| Пользователей | RAM | CPU | Диск |
|---------------|-----|-----|------|
| До 500 | 1GB | 1 CPU | 10GB |
| До 1,000 | 2GB | 1 CPU | 20GB |
| До 10,000 | 4GB | 2 CPU | 50GB |
| До 50,000 | 8GB | 4 CPU | 100GB |

### Оптимизация

- Включите Redis для кэширования (профиль `with-redis`)
- Настройте PostgreSQL для production
- Используйте nginx как reverse proxy
- Мониторьте ресурсы через `docker stats`

## 🤝 Поддержка

### Получить помощь

- 💬 **Telegram**: @fringg

### Вклад в проект

1. Fork репозитория
2. Создайте feature branch
3. Внесите изменения
4. Создайте Pull Request

## 📄 Лицензия

Этот проект распространяется под лицензией MIT. См. файл [LICENSE](LICENSE) для подробностей.

## 🗺 Roadmap & TODO

### 📋 Общий план развития

| № | Задача | Статус | Версия | Приоритет | Описание |
|---|---------|--------|--------|-----------|----------|
| 1 | Мониторинг подписок | ✅ Done | v1.1.0 | 🔴 High | Служба оповещения об истечении срока и автоконтроль |
| 2 | Платежные шлюзы | ✅ Done | v1.3.2 | 🔴 High | Звезды |
| 2.1 | Платежные шлюзы | 🎯 Planned | v1.4.0+ | 🔴 High | ЮKassa |
| 2.2 | Платежные шлюзы | 🎯 Planned | v1.4.0+ | 🟡 Medium | Сбербанк, Tinkoff, Crypto, Others |
| 3 | Синхронизация RemnaWave | ✅ Done | v1.1.0 | 🟡 Medium | Вывод информации о статусе панели remnawave и нод прямо в бота |
| 3 | Синхронизация RemnaWave | ✅ Done | v1.1.0 | 🟡 Medium | Импорт пользователей по Telegram ID + Синхранизация Панель->Бот |
| 4 | Веб-панель управления | 🎯 Planned | v1.4.0+ | 🟡 Medium | Полнофункциональный веб-интерфейс |
| 5 | Управление промокодами | ✅ Done | v1.3.0 | 🟢 Low | Удаление, редактирование |
| 6 | Безопасное удаление подписок | 🚧 In Progress | v1.4.0 | 🟡 Medium | Архивирование вместо удаления |
| 7 | Уведомления в другие чаты | 🎯 Planned | v1.5.0 | 🟡 Medium | Webhook, Email |
| 8 | Реферальная система | ✅ Done | v1.2.0 | 🟢 Low | Полнофункциональная программа с подробной статистикой |
| 9 | Рулетка | ✅ Done | v1.3.0 | 🟢 Low | Лудочка |
| 10 | Блокировка | 🚧 In Progress | v1.3.0+ | 🟢 Low | Бан/разбан юзеров |
| 11 | Удаление истекшик подписок из бота и панели | ✅ Done | v1.3.1 | 🔴 High | Дабы не плодить лишние записи в базе бота и панели ремны, да и в целом это логично)( |
| 12 | Правила сервиса | ✅ Done | v1.3.3 | 🟢 Low | Вывод правил сервиса в боте с конфигурацией через админку |
| 13 | Автоплатежи | ✅ Done | v1.3.3 | 🟡 Medium | Возможность включать-выключать автоплатежи и настраивать их + админская статистика |
| 14 | Все подписки юзеров | ✅ Done | v1.3.4 | 🟡 Medium | Возможность просматривать все подписки купленные юзерами в админ панели |


### 🚨 Возможные проблемы и пути и решения

#### Переход с версии 1.3.3 на 1.3.4

Может такое пройзойти, что после обновления образа у вас сломается база с подписками и в консоль полетят sql ошибки, дело в том, что в патче 1.3.4 добавились автоплатежи с доп полями в бд, во время обновления миграция может пройти некорректно(Я еще не до конца разобрался в чем проблема, но имейте в виду).

Для фикса в репозитории скачайте файлик emergency_fix.py и положите его рядом с докер файлом

В докер добавьте сервис:

    emergency-fix:
        image: fr1ngg/remnawave-bedolaga-telegram-bot:latest  # Используем тот же образ что и бот
        volumes:
          - ./emergency_fix.py:/app/emergency_fix.py
        environment:
          - DATABASE_URL=postgresql+asyncpg://remnawave_user:secure_password_123@postgres:5432/remnawave_bot #путь до DATABASE_URL
        networks:
          - bot_network
        depends_on:
          postgres: 
            condition: service_healthy
        profiles:
          - emergency  # Профиль, чтобы не запускался по умолчанию
        command: python emergency_fix.py

После выполните:

    docker compose run --rm emergency-fix

Скрипт добавит необходимые поля и починит вашу базу с подписками. После можете удалить секцию с emergency-fix и скрипт из докер файла.

**Для тех кто запускает бота через скрипт управления ботом добавлены кнопки для восстановления бд, 10) Экстренное исправление БД (Python) 11) Экстренное исправление БД (SQL)**

**⚠️ Важные замечания от автора:**

> 🗑 **Осторожно с удалением подписок!** Сейчас удаление плана подписки скроет эту подписку у всех пользователей, которые ее купили. Используйте деактивацию вместо удаления. Эта проблема будет исправлена в v1.4.0.

---

### 🚀 Хотите помочь?

**Разработчикам:**
- 🐛 Найдите и исправьте баги
- ✨ Предложите новые функции
- 📝 Улучшите документацию
- 🧪 Напишите тесты

**Пользователям:**
- 💭 Поделитесь идеями в Issues
- 🐞 Сообщите о найденных проблемах
- ⭐ Поставьте звезду проекту
- 📢 Расскажите друзьям

**Спонсорам:**
- 💰 Поддержите разработку
- 🎯 Закажите приоритетные функции
- 🏢 Корпоративная поддержка

---

**⭐ Если проект был полезен, поставьте звездочку на GitHub!**

---

### PS 

Автор не является проф. разработчиком, да и без вайбкодинга не обошлось, но я прикладываю все усилия, чтобы сделать удобного публичного бота для ваших сервисов)( 

*Создано с ❤️ для Remnawave сообщества*
