# Python_template_IDS706

# Python_template_IDS706

This repository provides a clean, modular Python project template tailored for IDS 706: Data Engineering Systems. It includes the necessary structure, tools, and automation to get you started with writing production-level Python code.

📦 Project Overview
This template helps students and developers:

Quickly spin up a Python project using either local development or GitHub Codespaces.

Integrate development best practices: testing, linting, formatting, and CI/CD.

Focus on writing code, not configuration.

🚀 Features
DevContainer support for GitHub Codespaces

Makefile for streamlined commands

Pre-configured pytest, flake8, black, and coverage

GitHub Actions CI for automation

Sample Python script and tests included

🛠️ Project Setup
You can follow either of the two workflows below.

1. Local Setup (Python Virtual Environment)
bash
Copy
Edit
# Clone the repo
git clone https://github.com/YOUR_USERNAME/IDS706_python_template.git
cd IDS706_python_template

# (Optional but recommended) Create and activate a virtual environment
python3 -m venv ~/.IDS706_python_template
source ~/.IDS706_python_template/bin/activate

# Install dependencies
make install
2. GitHub Codespaces (Dev Container)
Create a new repository on GitHub (e.g., IDS706_python_template)

Enable "Add a README file"

Click Codespaces > Create codespace on main

In VS Code, open the Command Palette (⇧⌘P) and select
Dev Containers: Add Development Container Configuration Files...

Choose the Python 3.11 template

Rebuild the container:
⇧⌘P → Dev Containers: Rebuild Container

Run make install in the terminal

📁 Project Structure
text
Copy
Edit
.
├── hello.py              # Sample Python script
├── test_hello.py         # Unit tests
├── Makefile              # Dev commands
├── requirements.txt      # Python dependencies
└── .devcontainer/        # (Optional) Dev container setup
🧪 Usage Examples
Sample Python Script (hello.py)
python
Copy
Edit
def say_hello(name: str) -> str:
    return f"Hello, {name}, welcome to Data Engineering Systems (IDS 706)!"

def add(a: int, b: int) -> int:
    return a + b
Sample Test (test_hello.py)
python
Copy
Edit
from hello import say_hello, add

def test_say_hello():
    assert say_hello("Annie") == "Hello, Annie, welcome to Data Engineering Systems (IDS 706)!"

def test_add():
    assert add(2, 3) == 5
✅ Makefile Commands
Command	Description
make install	Install dependencies
make test	Run unit tests with coverage
make lint	Run linting with flake8
make format	Auto-format code using black
make clean	Remove cache and temporary files
make all	Run install, format, lint, and test

🤖 GitHub Actions (CI/CD)
To enable CI:

Go to the Actions tab in your repo

Choose "Set up a workflow yourself"

Paste the following into .github/workflows/python.yml:

yaml
Copy
Edit
name: Python Template for IDS706

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - name: Set up Python
      uses: actions/setup-python@v5
      with:
        python-version: '3.11'
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt
    - name: Lint with flake8
      run: flake8 hello.py
    - name: Run tests
      run: pytest --cov=hello
Once committed, GitHub Actions will run automatically on every push or pull request!

💡 Additional Resources
GitHub Docs

GitHub Actions

Python Virtual Environments

VS Code Dev Containers

Makefile Tutorial

🙌 Acknowledgments
This template was built for IDS 706: Data Engineering Systems at Duke University to promote industry-standard workflows for modern Python development.


[![Python Template for IDS706](https://github.com/zhongyuan-duke/IDS-706-week-1-template/actions/workflows/main.yml/badge.svg)](https://github.com/zhongyuan-duke/IDS-706-week-1-template/actions/workflows/main.yml)

## Create your first project for Data Engineering Systems (IDS 706)

## Two approaches:

#### GitHub Repo Python Template (Local Setup Workflow)

- Clone/Start the repository locally or use GitHub Codespaces without a container.
- Set up a Python virtual environment (optional) and install dependencies using either pip install -r requirements.txt or make install.

#### Cloud-based Containerized Setup Workflow (With Dev Container)

- Create a GitHub repository.
- Launch a Codespace from the repository.
- Add a Dev Container configuration using VS Code.
- Rebuild the container to apply changes.

Once your environment is ready, the following steps are common to both approaches:

- Create project files: Makefile, XX.py, test_XX.py, and requirements.txt.
- Write your Python code and tests in the appropriate files.
- Run Makefile commands as needed: make install, make test, make format, make lint, make clean.
- Commit and push your changes to GitHub.
- Enable GitHub Actions for automation/Continuous Integration.

## Create a new GitHub Repository
1. Go to [GitHub](https://github.com) and create a new repository named e.g., `IDS706_python_template`.      
   - Make sure to select "Public" or "Private" based on your preference.
   - Optionally, add a description.  
2. enable the "Add a README file" option.
3. Click on "Create repository".
4. Click codespaces and then "Create codespace on main".

## Create new files in the repository (using the terminal or manually)
```bash
touch Makefile
touch hello.py
touch test_hello.py
touch requirements.txt
```

## Setup Python Environment (if you're not using a Dev Container)
If you're working outside of a dev container, you can manually create and activate a virtual environment. If you do so, for consistency, it's recommended to name the environment the same as your repository.

```bash
python3 -m venv ~/.IDS706_python_template
source ~/.IDS706_python_template/bin/activate
```


## Create a Makefile
```makefile
install:
	pip install --upgrade pip &&\
		pip install -r requirements.txt

format:
	black *.py

lint:
	flake8 hello.py

test:
	python -m pytest -vv --cov=hello test_hello.py

clean:
    rm -rf __pycache__ .pytest_cache .coverage

all: install format lint test

```
## Create a requirements.txt file
```text
pylint
flake8
pytest
click
black
pytest-cov
```

## VS Code Dev Containers (Suggested)
Open a sample in a container by pressing shift+command+P, then select `Dev Containers: Add Development Container Configuration Files...`. Choose the Python 3.11 template, and it will create the necessary files for you.

#### Rebuild or update your container
after you make changes to your container, such as installing a packages, you'll rebuild your container for your changes to take effect. by pressing shift+command+P, then select `Dev Containers: Rebuild Container` or `Codespaces: Rebuild Container` command so the modifications are picked up.  


## Run the Makefile (required if you do not use Dev Containers)
```bash 
make install
```


## Create a simple Python script
```python
def say_hello(name: str) -> str:
    """Return a greeting message to students in the IDS class."""
    return f"Hello, {name}, welcome to Data Engineering Systems (IDS 706)!"


def add(a: int, b: int) -> int:
    """Return the sum of two numbers."""
    return a + b
```

## Create a test file
```python
from hello import say_hello, add

def test_say_hello():
    assert (
        say_hello("Annie")
        == "Hello, Annie, welcome to Data Engineering Systems (IDS 706)!"
    )

def test_add():
    assert add(2, 3) == 5
```

## Run the tests
```bash 
make test
``` 
## Format the code
```bash 
make format
```
## Lint the code
```bash
make lint
```
## Clean up the environment
```bash
make clean
```
## Commit and push your changes via commands or User Interface
```bash
git add .
git commit -m "Initial commit with Python template setup"   
git push origin main
``` 
## View your repository

## Enable GitHub Actions

1. Go to your repository on GitHub.
2. Click on the "Actions" tab.
3. Click on "New workflow".
4. Select "Set up a workflow yourself".
5. Replace the content with the following YAML configuration:

```yaml
name: Python Template for IDS706

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v4
    - name: Set up Python
      uses: actions/setup-python@v5
      with:
        python-version: '3.11'
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt
    - name: Lint with flake8
      run: flake8 hello.py
    - name: Run tests
      run: pytest --cov=hello

```
6. Commit and push this file to your repository.
7. GitHub Actions will run automatically on every push or pull request!

## View the Actions tab 

1. Go to the "Actions" tab in your repository.
2. You should see the workflow running.
3. Click on the latest workflow run to see the details.


## Congratulations!
You have successfully created a Python template project for Data Engineering Systems (IDS 706) using GitHub, Codespaces, and GitHub Actions. You can now use this template for your future projects in the course.

This template provides a structured way to set up a Python project with essential tools for development, testing, and continuous integration. It includes:
- A `Makefile` for easy command execution.
- A virtual environment setup for dependency management.
- A devcontainer configuration for GitHub Codespaces
- A simple Python script with functions.
- Unit tests to ensure code correctness.
- GitHub Actions for continuous integration to automate linting and testing.
- Github Copilot for AI-assisted coding.

## Additional Resources
- [GitHub Documentation](https://docs.github.com/en)
- [Python Virtual Environments](https://docs.python.org/3/tutorial/venv.html)
- [Installing Python and conda](https://www.practicaldatascience.org/notebooks/PDS_not_yet_in_coursera/00_setup_env/setup_python.html)
- [Setting Up Visual Studio Code](https://www.practicaldatascience.org/notebooks/PDS_not_yet_in_coursera/00_setup_env/setup_vscode.html)
- [GitHub Dev-Container Documentation](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/setting-up-your-python-project-for-codespaces)
- [Makefile Documentation](https://www.gnu.org/software/make/manual/make.html)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)

## Acknowledgments
This template was created as part of the Data Engineering Systems (IDS 706) course to help students set up their projects efficiently using modern development practices.   
