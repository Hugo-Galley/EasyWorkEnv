<div align="center">

# EasyWorkEnv

**The simplest way to manage environment variables in Python.**

[![PyPI version](https://img.shields.io/pypi/v/easyworkenv?color=blue&label=PyPI)](https://pypi.org/project/easyworkenv/)
[![Python](https://img.shields.io/pypi/pyversions/easyworkenv?label=Python)](https://pypi.org/project/easyworkenv/)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-green.svg)](https://www.gnu.org/licenses/gpl-3.0)

Load `.env`, `.json`, and `.yaml` config files in one line of code.
Access your variables with clean dot notation — no more `os.getenv()` boilerplate.

</div>

---

## Why EasyWorkEnv?

Managing environment variables in Python shouldn't be painful. Most solutions either force you into a single file format, require verbose syntax, or lack support for nested configurations.

**EasyWorkEnv** solves this by providing:

- **Multi-format support** — `.env`, `.json`, and `.yaml` out of the box
- **Dot notation access** — `config.DATABASE.HOST` instead of `config["DATABASE"]["HOST"]`
- **Nested configuration** — structure your settings with unlimited depth
- **Zero config** — just point to your file, it works
- **Lightweight** — only one dependency (`PyYAML`)
- **Python 3.8+** compatible

---

## Installation

```bash
pip install easyworkenv
```

---

## Quick Start

```python
from EasyWorkEnv import Config

config = Config(".env")

# Access your variables directly as attributes
print(config.API_KEY)
print(config.DATABASE_URL)
```

That's it. One import, one line of setup.

---

## Usage Examples

### `.env` file

```env
# .env
APP_NAME=MyApp
SECRET_KEY=super-secret-value
DEBUG=true
DATABASE_URL=postgresql://localhost:5432/mydb
```

```python
from EasyWorkEnv import Config

config = Config(".env")

print(config.APP_NAME)       # "MyApp"
print(config.SECRET_KEY)     # "super-secret-value"
print(config.DATABASE_URL)   # "postgresql://localhost:5432/mydb"
```

### `.json` file (with nested config)

```json
{
  "APP_NAME": "MyApp",
  "DATABASE": {
    "HOST": "localhost",
    "PORT": 5432,
    "NAME": "mydb"
  },
  "API_KEY": "sk-abc123"
}
```

```python
from EasyWorkEnv import Config

config = Config("config.json")

print(config.APP_NAME)        # "MyApp"
print(config.DATABASE.HOST)   # "localhost"
print(config.DATABASE.PORT)   # 5432
print(config.API_KEY)         # "sk-abc123"
```

### `.yaml` file (with nested config)

```yaml
# config.yaml
APP_NAME: MyApp
DATABASE:
  HOST: localhost
  PORT: 5432
  NAME: mydb
REDIS:
  URL: redis://localhost:6379
```

```python
from EasyWorkEnv import Config

config = Config("config.yaml")

print(config.APP_NAME)        # "MyApp"
print(config.DATABASE.HOST)   # "localhost"
print(config.REDIS.URL)       # "redis://localhost:6379"
```

---

## Supported File Formats

| Format  | Extension | Nested Config | Comments |
|---------|-----------|:------------:|:--------:|
| dotenv  | `.env`    | No           | Yes      |
| JSON    | `.json`   | Yes          | No       |
| YAML    | `.yaml`   | Yes          | Yes      |

---

## Contributing

Contributions are welcome! If you'd like to help improve EasyWorkEnv:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/my-feature`)
3. **Commit** your changes (`git commit -m "Add my feature"`)
4. **Push** to the branch (`git push origin feature/my-feature`)
5. **Open** a Pull Request

---

## License

This project is licensed under the **GNU General Public License v3.0** — see the [LICENSE](./LICENSE) file for details.

---

<div align="center">

Made by [Hugo Galley](https://github.com/Hugo-Galley)

</div>
