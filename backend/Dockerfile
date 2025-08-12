FROM python:3.12

# Установка зависимостей
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    python3-distutils \
    && rm -rf /var/lib/apt/lists/*

# Создание и настройка рабочей директории
WORKDIR /app

RUN pip install gunicorn==23.0.0

# Копирование и установка зависимостей
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Копирование остальных файлов проекта
COPY . .

# Команда запуска
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"]
