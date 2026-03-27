FROM python:3.11-slim

WORKDIR /app

RUN apt-get update && apt-get install -y \
    gcc \
    libpq-dev \
    && rm -rf /var/lib/apt/lists/*

COPY backend/requirements.txt .
RUN pip install --upgrade pip && pip install -r requirements.txt

COPY backend/ .

RUN python manage.py collectstatic --noinput

CMD ["gunicorn", "kittygram_backend.wsgi:application", "--bind", "0:8000"]
