###  Installation Guide

Navigate to the lab folder and create a virtual environment:

```bash
# Windows - Try these commands in order until one works:
cd labs/1_mlflow

# Option 1: Using Python Launcher
py -3.10 -m venv venv

# Option 2: Direct python command
python -m venv venv

# Option 3: Full path (adjust path to your Python installation)
C:\Python310\python.exe -m venv venv

# Activate
venv\Scripts\activate

# Verify Python Version
python --version  # Should show Python 3.10.x

# Install Dependencies
pip install -r requirements.txt

# macOS/Linux
cd labs/1_mlflow
python3.10 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```