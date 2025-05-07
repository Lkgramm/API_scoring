# Scoring API

HTTP API сервис для подсчёта скоринга пользователей.
Позволяет отправлять POST-запросы на методы `/method/online_score` и `/method/clients_interests`, с проверкой авторизации и валидацией данных.

## Функционал

- Авторизация через токен
- Валидация полей (email, телефон, дата рождения и т.д.)
- Метод `online_score` — возвращает скоринг пользователя
- Метод `clients_interests` — возвращает интересы клиентов
- Поддержка тестирования и логирования
- Настроен CI/CD через GitHub Actions
- Используется Poetry для управления зависимостями

---

## Технологии

- Python 3.8+
- `poetry` — управление пакетами и зависимостями
- `pytest` — тестирование
- `pre-commit` — форматирование и проверка кода перед коммитом
- `black`, `flake8`, `mypy`, `pyupgrade` — улучшение качества кода
- GitHub Actions — автоматическое тестирование

---

## 📦 Установка

1. Клонируй репозиторий:

```bash
git clone https://github.com/yourname/api-scoring.git
cd api-scoring
```

2. Установи зависимости:

```bash
poetry install
```

3. (Опционально) Настрой `pre-commit`:

```bash
pre-commit install
```

---

## Запуск сервера

```bash
make run
```

Сервер будет доступен по адресу: `http://127.0.0.1:8080/method/`

---

## Тестирование

Запуск юнит-тестов:

```bash
make test
```

Также можно запустить отдельный тест:

```bash
poetry run pytest tests/test.py -v
```

---

## Линтинг и форматирование

Проверка и форматирование кода:

```bash
make lint
make format
```

## 🌐 Пример запроса

```bash
curl -X POST http://127.0.0.1:8080/method/ \
  -H "Content-Type: application/json" \
  -d '{
        "account": "horns&hoofs",
        "login": "admin",
        "method": "online_score",
        "token": "55cc9ce545bcd144300fe9efc28e65d415b923ebb6be1e19d2750a2c03e80dd209a27954dca045e5bb12418e7d89b6d718a9e35af34e14e1d5bcd5a08f21fc95",
        "arguments": {
          "phone": "79175002040",
          "email": "stupnikov@otus.ru"
        }
      }'
```

---

## 🧬 CI/CD

Проект настроен с использованием **GitHub Actions**:
- Автоматический запуск тестов при пуше или Pull Request'е
- Проверка стиля и типов
- Форматирование кода

---

# Дополнительно

| Команда            | Описание                             |
|--------------------|--------------------------------------|
| `make lint`        | Проверка стиля кода                  |
| `make format`      | Форматирование кода (`black`)        |
| `make clean`       | Очистка временных файлов             |

---
