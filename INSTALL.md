# Установка TeleOSINT

## Windows

```powershell
# 1. Установите Python 3.10+ с python.org
# 2. Откройте PowerShell и выполните:
git clone https://github.com/yourname/teleosint
cd teleosint
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
copy config.example.ini config.ini
```

Откройте `config.ini` в блокноте, вставьте ваши Telegram API-ключи и запустите:
```powershell
python teleosint.py
```

## Linux / macOS

```bash
git clone https://github.com/yourname/teleosint
cd teleosint
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
cp config.example.ini config.ini
nano config.ini   # вставьте API-ключи
python3 teleosint.py
```

## Получение Telegram API-ключей

1. Перейдите на https://my.telegram.org
2. Войдите в аккаунт через SMS
3. Нажмите **API development tools**
4. Заполните форму (app_title: любое, short_name: любое)
5. Скопируйте `api_id` и `api_hash` в `config.ini`

## Установка через Docker

```bash
docker build -t teleosint .
docker run -it -v $(pwd)/results:/app/results teleosint
```

## Зависимости

```
telethon>=1.34
requests>=2.31
pandas>=2.0
networkx>=3.1
matplotlib>=3.7
openpyxl>=3.1
tqdm>=4.65
colorama>=0.4
```

## Устранение проблем

**Ошибка: `FloodWaitError`** — Telegram временно ограничил запросы. Подождите указанное время.

**Ошибка: `SessionPasswordNeededError`** — Включена двухфакторная аутентификация. Введите пароль при первом запуске.

**Не работает через Tor** — Убедитесь, что Tor Browser или Tor daemon запущен на порту 9050.
