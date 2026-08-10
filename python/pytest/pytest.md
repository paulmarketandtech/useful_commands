1. Install
```
uv add --dev pytest pytest-mock pytest-cov
```
2. pyproject.toml — tell pytest where things live:
```
[tool.pytest.ini_options]
pythonpath = ["src"]
testpaths = ["tests"]
```
3. Run everything with:
```
uv run pytest -v
uv run pytest --cov=stock_market --cov-report=term-missing
```
