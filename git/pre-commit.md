### Example basic usage with uv (not pip)
```
touch .pre-commit-config.yaml

repos:
  # Ruff (official mirror – recommended)
  - repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.16.2     # pin to a specific Ruff version (update with `pre-commit autoupdate`)
    hooks:
      - id: ruff-check
        args: [--fix]   # auto-fix what it can
      - id: ruff-format

  # pytest (local hook so it uses your project's environment via uv)
  - repo: local
    hooks:
      - id: pytest
        name: pytest
        entry: uv run pytest
        language: system
        types: [python]
        pass_filenames: false   # let pytest discover tests itself
        # optional: always_run: true   # run even if no Python files changed
```

### Useful commands
```
# Run all hooks on every file (good for first-time check)
uvx pre-commit run --all-files

# Run only a specific hook
uvx pre-commit run ruff-check --all-files
uvx pre-commit run pytest --all-files

# Update the `rev` pins to the latest tagged versions
uvx pre-commit autoupdate

# Temporarily skip hooks for one commit
git commit --no-verify -m "..."
```
