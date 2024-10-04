install:
	pip3 install --upgrade pip
	pip3 install -r requirements.dev.txt
	pip3 install -r requirements.txt
.PHONY: install

check-format:
	black --check .
	autoflake --check --quiet --remove-all-unused-imports --remove-unused-variables --recursive .
.PHONY: check-format

format:
	autoflake --in-place --remove-all-unused-imports --remove-unused-variables --recursive .
	isort .
	black .
.PHONY: format

test:
	PYTHONPATH=$(realpath ./src) pytest tests
.PHONY: test

deploy-dev:
	python3 deployment.py dev
.PHONY: deploy-dev

deploy-prod:
	python3 deployment.py prod
.PHONY: deploy-prod

local-debug:
	cd src/ && functions-framework --target main --debug  --port 8080
