# uv

## Installation
macOS/Linux:
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```
Windows:
```bash
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```
pip:
```bash
pip install uv
```
Homebrew:
```bash
brew install uv
```

## Project & Dependency Management
Initialize a project:
```bash
uv init my-project
```
Add & remove deps:
```bash
uv add requests
uv add --dev pytest
uv remove requests
```
Lock & sync dependencies:
```bash
uv lock
uv lock --upgrade-package package1
uv sync
```
Run commands in project environment:
```bash
uv run python main.py
uv run python -m package.main
uv run pytest
```

## Virtual Environments & Pip Interface
Create a venv:
```bash
uv venv
uv venv --python 3.11
```
Install packages (pip style):
```bash
uv pip install requests numpy
uv pip install -r requirements.txt
```