# Создание полноценного dev-env в каждом новом проекте

### Используются штуки:
- **poetry** - менеджер пакетов и окружений
- **pre-commit** - хуки на коммит
- **flake8** - линтер
- **black** - авто-форматирование кода 
- **mypy** - проверка на type hintings
- **isort** - сортировка импортов

С помощью pre-commit каждый ```commit -m "init"``` проходит через все проверки (линтер, форматирование, проверка на размер и тд)  

### Install nightly poetry
```
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python -
poetry self update --preview
```
*Preview version for add git dependences*

### Install environment with dev dependences  
```
poetry init
poetry env use python3.10
poetry shell
poetry add --dev pytest-cov pre-commit flake8 isort black mypy
```

### Config examples:
- [pyproject.toml](./add-to-config/pyproject.toml)
- [setup.cfg](./add-to-config/setup.cfg)
- [.pre-commit-config.yaml](./add-to-config/.pre-commit-config.yaml)

```
cat add-to-config/pyproject.toml >> project/pyproject.toml
cat add-to-config/.pre-commit-config.yaml >> project/.pre-commit-config.yaml
cat add-to-config/setup.cfg >> project/setup.cfg
```

### Normal .gitignore + enable autoupdate pre-commit
```
pre-commit install
pre-commit autoupdate
pre-commit run --all-files
git add .
git commit -m 'Initial commit'
```
