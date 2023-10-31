
# python project setup

## `asdf`

`asdf` is a CLI tool that can manage multiple language runtime versions on a per-project basis. It is like `gvm`, `nvm`, `rbenv` & `pyenv` (and more) all in one! Simply install your language's plugin!


### `asdf` installation

```bash
brew install asdf
```

To use asdf, add the following line (or equivalent) to your shell profile.
e.g. ~/.profile or ~/.zshrc
    . /usr/local/opt/asdf/libexec/asdf.sh
e.g. ~/.config/fish/config.fish
     source /usr/local/opt/asdf/libexec/asdf.fish
Restart your terminal for the settings to take effect.

### install `python` locally

```bash
# add python to asdf
asdf plugin add python
# install specific version of python using asdf
asdf install python 3.11.6
# setup python 3.11.6 as a global interpreter.
asdf global python 3.11.6
```

to list and install other version

```bash
# show locally installed versions
asdf list python
# show all installable versions
asdf list all python
```

### setup `shell` to use `asdf`

ZSH (oh-my-zsh, MAC)

```bash
# add `asdf` to plugins
plugins=(git asdf)
```

Bash (MAC)

pre-configured.

## `poetry` and `ruff`

### installation

- poetry
    - Python packaging and dependency management made easy
- ruff
    - An extremely fast Python linter and code formatter, written in Rust.
- black
    - Black is the uncompromising Python code formatter. By using it, you agree to cede control over minutiae of hand-formatting. In return, Black gives you speed, determinism, and freedom from pycodestyle nagging about formatting. You will save time and mental energy for more important matters.
- mypy
    - Optional static typing for Python

```bash
pip install poetry ruff
```

### initialize an existing project using `poetry`

```bash
poetry init
# answer to the prompt poetry asks
# avoid too general project name (e.g., python)
```

### `poetry` usage

To install a package as a dependency of the project.

```bash
poetry add <dep_name>
```

To install a package as a dev dependency of the project.

```bash
poetry add <dep_name> --group dev
```

To lock the versions of dependencies of the project.

```bash
poetry lock
# `poetry add` implies `poetry lock`
```

To install dependencies of the project from `poetry.lock`

```bash
poetry install
```

To run a shell with virtualenv

```bash
poetry shell
```

To run a command under the virtualenv

```bash
poetry run <command>
```


### recommended initial configuration

install `ruff`, `black`, `mypy`, `isort`, `rope`

```bash
# when you install dependencies for the project, use `poetry add` instead of `pip install`
poetry add ruff black mypy isort rope --group dev
```

add following lines to `pyproject.toml` file.
```toml
[tool.ruff]
line-length = 120
target-version = 'py311'
select = ["E", "F", "W", "N", "B", "I", "NPY", "PL", "C90", "UP", "SIM", "RUF"]

[tool.ruff.mccabe]
# default: 10
max-complexity = 12

[tool.black]
line-length = 120
target-version = ['py39', 'py310', 'py311']

[tool.mypy]
# be strict
disallow_untyped_calls = true
warn_return_any = true
strict_optional = true
warn_no_return = true
warn_redundant_casts = true
warn_unused_ignores = true

disallow_untyped_defs = true
check_untyped_defs = true

```


## `vscode` setup

### install extensions

- `python`
- `ruff`
- `mypy type checker`
- `black formatter`

### uninstall extensions

- `pylance` (installed by `python`)

### change python interpreter using poetry

