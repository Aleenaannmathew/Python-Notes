🟢 Python Virtual Environments — Detailed Guide

A virtual environment in Python is an isolated environment that allows you to manage dependencies, libraries, and Python versions for a project without affecting the system-wide Python installation.

It’s essential for project isolation, avoiding conflicts between package versions.

🔹 1. Why Use Virtual Environments?

Isolation: Each project can have its own dependencies without affecting other projects.

Version Control: You can use different package versions for different projects.

Avoid Conflicts: System-wide packages won’t interfere with project-specific packages.

Reproducibility: You can share requirements.txt to replicate the environment easily.

🔹 2. Creating Virtual Environments

Python provides multiple ways to create virtual environments:

2.1 Using venv (Python 3.3+ built-in module)
# Create a virtual environment named 'myenv'
python -m venv myenv


This creates a folder myenv/ containing:

bin/ or Scripts/ — executables

lib/ — installed packages

pyvenv.cfg — configuration file

2.2 Using virtualenv (external package)
pip install virtualenv

# Create a virtual environment
virtualenv myenv


Works for both Python 2 and 3.

Offers more customization options.

🔹 3. Activating Virtual Environments
3.1 Windows
myenv\Scripts\activate

3.2 macOS / Linux
source myenv/bin/activate


After activation, your terminal prompt changes to:

(myenv) $


All installed packages now go inside this environment.

🔹 4. Deactivating Virtual Environments
deactivate


Returns to the system’s default Python environment.

🔹 5. Installing Packages in a Virtual Environment
pip install requests


Packages are installed inside myenv only.

Use pip list to see installed packages in the environment.

🔹 6. Removing a Virtual Environment

Simply delete the environment folder:

rm -rf myenv        # macOS / Linux
rmdir /s /q myenv   # Windows

🔹 7. Sharing and Recreating Environments

Freeze packages to requirements.txt:

pip freeze > requirements.txt


Recreate the environment on another system:

python -m venv myenv
source myenv/bin/activate
pip install -r requirements.txt


Ensures identical package versions across machines.

🔹 8. Best Practices

One environment per project — never reuse environments.

Keep your requirements.txt updated.

Avoid installing packages globally when working on projects.

Consider using pip-tools or poetry for advanced dependency management.