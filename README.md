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

Use the exported config directly when you want the shared baseline without
project-specific overrides:

```bash
uv run mypy --config-file "$(uv run teo-mypy-config-path)" .
```

For projects that need plugins or module overrides, copy the baseline into the
project's own config and add local settings there. mypy does not merge multiple
config files, so this package intentionally does not document an inheritance
contract.

```toml
[tool.mypy]
python_version = "3.12"
strict = true
plugins = ["pydantic.mypy"]

[[tool.mypy.overrides]]
module = ["redis.*"]
ignore_missing_imports = true
```

Equivalent `mypy.ini` syntax:

```ini
[mypy]
python_version = 3.12
strict = true
plugins = pydantic.mypy

[mypy-redis.*]
ignore_missing_imports = true
```

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
