FROM python:3.11-slim

ENV HOME=/app \
    POETRY_NO_INTERACTION=1 \
    POETRY_VIRTUALENVS_IN_PROJECT=1 \
    POETRY_VIRTUALENVS_CREATE=1 \
    POETRY_CACHE_DIR=/tmp/poetry_cache \
    PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1

WORKDIR $HOME

RUN pip install --upgrade pip && pip install poetry==1.8.3

COPY pyproject.toml poetry.lock $HOME/

RUN poetry export -f requirements.txt --output requirements.txt && pip install -r requirements.txt

COPY . $HOME

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "hometap.wsgi:application"]
