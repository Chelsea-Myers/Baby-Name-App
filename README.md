# Baby Name App Project Instructions

## Part 1: Install Ubuntu (Windows Subsystem for Linux – WSL)
1. **Enable WSL and Required Features via Windows Features**
   - Open the Windows search bar.
   - Type “Turn Windows features on or off” and click on the matching result to open the Windows Features dialog.
   - Scroll through the list and check the boxes next to:
     - `Windows Subsystem for Linux`
     - `Virtual Machine Platform`
     - `Hyper-V`
2. Click “OK” to apply the changes.
3. Restart your computer if prompted.
4. **Download and Install Ubuntu on Windows**
   - Download Ubuntu for free from the Microsoft Store.
   - If you have installed and uninstalled Ubuntu in the past, you may need to do the following in PowerShell:
     - Run: `wsl --unregister ubuntu`
     - Run: `wsl --install`
5. Enter a Linux username and password. Don’t forget them!

## Part 2: Create an Account in GitHub
1. Visit [GitHub.com](https://github.com/) and follow the sign-up process.

## Part 3: Install VS Code (Visual Studio Code) and Enable Python, WSL, and GitHub Repositories
1. **Download VS Code**
   - Download and install VS Code from the [Visual Studio Code website](https://code.visualstudio.com/).
2. **Install the Python Extension for VS Code**
   - Open Extensions (`Ctrl+Shift+X`) in VS Code and install the Python extension provided by Microsoft.
3. **Install Remote – WSL Extension**
   - In Extensions, search for and install the "Remote - WSL" extension.
4. **Install GitHub Repositories Extension for Visual Studio Code**
   - In Extensions, search for "GitHub Repositories" by GitHub.
5. **Sign in to GitHub**
   - Open the Command Palette by pressing `Ctrl+Shift+P`.
   - Type `GitHub: Sign in` and select the command.
   - Follow the instructions to authenticate with GitHub.

## Part 4: Fork the Baby-Name-App-Project-Files Repo
1. Navigate to [Baby Name App Project Files](https://github.com/Chelsea-Myers/Baby-Name-App-Project-Files) and click “Fork.”
   - Forking creates a personal copy of the project.
   - Copy the location of your fork by clicking "Code" and copying the provided HTML link.

## Part 5: Clone the Repo
1. Open the Command Palette (`Ctrl+Shift+P`) and type `WSL: Open Folder in WSL`.
   - Navigate to the directory where you want to download the project files.
2. Open a new terminal in VS Code.
3. **Change the Terminal to WSL**
   - Click on the down arrow next to the `+` and select WSL.
4. Clone the Baby-Name-App repo:
   - Run: `git clone <link to your repo>` (e.g., `https://github.com/username/Baby-Name-App-Project-Files`).
5. Verify the directory in the Explorer menu on the left.
6. Open the new project folder using `WSL: Open Folder in WSL`.

## Part 6: Set up a Virtual Environment
1. **Install Prerequisites**
   - Run: `sudo apt update`
   - Run: `sudo apt install python3 python3-pip`
2. Check Python and pip versions:
   - Run: `python3 --version`
   - Run: `pip3 --version`
3. **Create a Virtual Environment**
   - Navigate to the project directory.
   - Run: `python3 -m venv venv`
4. **Activate the Virtual Environment**
   - Run: `source venv/bin/activate`
   - You should see `(venv)` in the terminal prompt.
5. **Install Project Dependencies**
   - Run: `pip install -r requirements.txt`

## Part 7: Open and Edit the Project Files in VS Code
1. In the Explorer, locate the files `data`, `static`, `app.py`, and others.
2. Open `app.py`.
3. Add the following code under the comment:
   ```python
   # Extract year and rank in year for the given name-sex combination
   name_subset = babynames[(babynames['name'] == name) & (babynames['sex'] == sex)]
   name_years = name_subset['year'].tolist()
   name_ranks = name_subset['rank_in_year'].tolist()
4. Save the file.

## Part 8: Commit the Changes to GitHub
1. Click on **Source Control** in VS Code.  
   a. Enter a commit message and click **Commit and Push**.

## Part 9: Run the Flask App Locally
1. Start the Flask app:  
   - Run: `flask --app app --debug run`  
2. View the app at [http://localhost:5000](http://localhost:5000) in your browser.

## Part 10: Set Up Your App on PythonAnywhere
1. Delete the `venv` folder and zip the project directory.  
2. Create a PythonAnywhere account.  
3. Follow PythonAnywhere's instructions to upload, unzip, and configure your app.  

## Part 11: Set Up a Virtual Environment on PythonAnywhere
1. Open a Bash console.  
2. Run: `virtualenv venv`  
3. Activate the virtual environment:  
   - Run: `source venv/bin/activate`  
4. Install dependencies:  
   - Run: `pip install -r requirements.txt`

## Part 12: Deploy the App
1. Update the WSGI configuration file as follows:  
   ```python
   import sys
   path = '/home/yourusername/Baby-Name-App'
   if path not in sys.path:
       sys.path.append(path)
   from app import app as application