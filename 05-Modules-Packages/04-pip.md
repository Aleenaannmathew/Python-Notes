🟢 Python pip — Detailed Guide

pip is Python's package installer, used to install, upgrade, and manage third-party libraries. It is an essential tool for Python development.

🔹 1. What is pip?

pip stands for "Pip Installs Packages".

It allows you to download and install Python packages from the Python Package Index (PyPI).

Installed by default in Python 3.4+.

Works with both Python 2 and Python 3 (though Python 2 support is deprecated).

🔹 2. Checking pip Version
pip --version
pip3 --version   # For systems with both Python2 & Python3


Shows installed pip version and Python path.

🔹 3. Installing Packages
3.1 Install the latest version of a package
pip install requests

3.2 Install a specific version
pip install requests==2.28.1

3.3 Upgrade a package
pip install --upgrade requests

3.4 Install multiple packages at once
pip install numpy pandas matplotlib

3.5 Install from a requirements file
pip install -r requirements.txt


requirements.txt contains a list of packages and versions:

numpy==1.26.0
pandas==2.1.0
matplotlib>=3.8.0

🔹 4. Uninstalling Packages
pip uninstall requests


You can uninstall multiple packages at once:

pip uninstall numpy pandas

🔹 5. Searching Packages
pip search <package_name>


Note: pip search is deprecated in newer versions.

Alternatively, use https://pypi.org
 to search packages.

🔹 6. Listing Installed Packages
pip list


Shows all installed packages and their versions.

pip show requests


Shows detailed info about a single package (location, dependencies, version).

🔹 7. Freezing Installed Packages
pip freeze


Generates a list of installed packages suitable for requirements.txt:

pip freeze > requirements.txt

🔹 8. Best Practices with pip

Use virtual environments to avoid system-wide package conflicts:

python -m venv myenv
source myenv/bin/activate    # Linux/macOS
myenv\Scripts\activate       # Windows


Always upgrade pip to latest version:

pip install --upgrade pip


Avoid mixing pip and conda in the same environment.

Prefer specific versions in requirements.txt for reproducibility.

🔹 9. Troubleshooting pip

Permission errors:

pip install <package> --user


SSL certificate issues: Upgrade pip:

python -m pip install --upgrade pip


Proxy issues:

pip install <package> --proxy http://user:pass@proxy:port
