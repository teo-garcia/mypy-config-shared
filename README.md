<div align="center">

# teo-mypy-config-shared

**Shared mypy configuration for strict Python type checking**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PyPI](https://img.shields.io/pypi/v/teo-mypy-config-shared?color=blue)](https://pypi.org/project/teo-mypy-config-shared)
[![Python](https://img.shields.io/badge/Python-3.12+-3776AB?logo=python&logoColor=white)](https://python.org)

Part of the [@teo-garcia/templates](https://github.com/teo-garcia/templates) ecosystem

</div>

---

## Settings

| Setting | Value |
| --- | --- |
| **Target** | Python 3.12 |
| **Mode** | strict |

---

## Requirements

- Python 3.12+
- mypy 1.14+

---

## Usage

Install as a dev dependency:

```bash
uv add --dev teo-mypy-config-shared
```

Get the path to the installed config file:

```bash
uv run teo-mypy-config-path
```

Use `extends` in your project's `mypy.ini` (mypy supports `extends` in `.ini` format, not in `pyproject.toml`):

```ini
[mypy]
extends = /path/from/teo-mypy-config-path
plugins = pydantic.mypy

[[mypy.overrides]]
module = ["redis.*"]
ignore_missing_imports = true
```

For a portable setup, generate a `mypy.extend.ini` (gitignored) via Makefile:

```makefile
mypy-config:
    @printf "[mypy]\nextends = %s\n" "$(shell uv run teo-mypy-config-path)" > mypy.extend.ini
```

Then your `mypy.ini` at project root:

```ini
[mypy]
extends = mypy.extend.ini
# project-specific overrides below
```

Add `mypy.extend.ini` to `.gitignore`.

---

## Related Packages

| Package | Description |
| --- | --- |
| `teo-ruff-config-shared` | Ruff lint and format settings |
| `teo-pytest-config-shared` | pytest and coverage settings |

---

## License

MIT

---

<div align="center">
  <sub>Built by <a href="https://github.com/teo-garcia">teo-garcia</a></sub>
</div>
