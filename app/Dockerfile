FROM python:3.11.4-slim

EXPOSE 8000

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
ENV POETRY_VERSION=1.8.3

WORKDIR /code

COPY pyproject.toml poetry.lock ./

RUN pip install poetry==${POETRY_VERSION} && poetry config virtualenvs.create false

RUN poetry install --no-interaction --no-root

COPY . .
