
.PHONY: install
install:
	$(call log, installing packages)
	poetry install --no-dev


.PHONY: format
format:
	$(call log, reorganizing imports & formatting code)
	poetry run black .
	poetry run isort .
	poetry run ruff . --fix --exit-zero
	poetry run pre-commit run --all
	poetry run mypy .

.PHONY: migrations
migrations:
	$(call log, Started make migrations)
	poetry run alembic revision --autogenerate -m "$(filter-out $@,$(MAKECMDGOALS))"

.PHONY: migrate
migrate:
	$(call log, Started migrate)
	poetry run alembic upgrade head

.PHONY: run
run:
	poetry run python run.py
