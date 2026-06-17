* Тема проекта: MediaResizer — асинхронный микросервис оптимизации изображений
* Формат работы: В команде (2 человека)
* Состав команды и роли:
  - Колупаев Ефим: Тимлид, Архитектор / DevOps
    (проектирование, Docker/docker-compose, настройка Redis + Celery,
     система логирования, ревью Pull Request'ов)
  - Бердюгин Евгений: Backend-разработчик / QA-инженер
    (REST API на FastAPI, логика обработки изображений,
     написание тестов, документация Swagger/README)

2. ВЫБРАННЫЙ СТЕК ТЕХНОЛОГИЙ
* Язык программирования: Python 3.12
* Основной фреймворк/библиотеки:
  - FastAPI + Uvicorn — REST API-приёмник с авто-документацией (OpenAPI/Swagger)
  - Celery + Redis — асинхронная очередь задач (приём картинки → фоновая обработка)
  - Pillow + pillow-avif-plugin — сжатие, конвертация в WebP/AVIF,
    генерация разрешений (thumbnail / mobile / desktop)
  - Pydantic + pydantic-settings — валидация запросов и изоляция конфигурации
* Система логирования: Loguru
  (потоки INFO/ERROR/CRITICAL, вывод в stdout для Docker + ротируемые файлы)
* Линтер (статический анализ): Ruff
* Дополнительно (QA / контейнеризация):
  - pytest + pytest-asyncio + httpx — тестирование API и обработчиков
  - python-dotenv + .env.example — безопасное хранение секретов
  - Docker + docker-compose (сервисы: api, worker, redis) — запуск одной командой
