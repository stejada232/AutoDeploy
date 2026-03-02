# Mini Deploy

Mini Deploy is a lightweight, GUI-based Python application designed for one-way file deployment over SFTP. It allows you to connect to a remote server, browse local and remote directories side-by-side, and automatically push changes from your local machine to the server using a background observer.

## ✨ Features

* **Simple GUI Interface:** Built with Tkinter for an easy-to-use, split-pane file browsing experience.
* **Secure SFTP Protocol:** Securely transfers files using Paramiko's `SSHClient` with automatic host key verification.
* **Real-Time Auto-Deploy:** Utilizes Watchdog to monitor a selected local directory. Any file modifications, creations, renames, or deletions are instantly mirrored to the remote server.
* **Smart Debouncing:** Built-in timers prevent the server from being spammed with multiple uploads during rapid file-save sequences.
* **Thread-Safe UI:** Network operations and file syncing run on background threads, ensuring the interface remains fast and responsive.
* **Activity Logging:** An embedded log console tracks all connection statuses, file uploads, and errors in real-time.

## 📋 Prerequisites

To run this application, you will need **Python 3.x** installed on your system along with a few external libraries. 

You can install the required dependencies using your terminal:

    pip install paramiko watchdog

*(Note: `tkinter` is included in the standard Python library, but on some Linux distributions, you may need to install it separately via your package manager, e.g., `sudo apt-get install python3-tk`).*

## 🚀 Usage

1. Run the script from your terminal:
    
    python deploy_window.py

2. **Connect to Server:** Enter your server's IP, Port (usually 22 for SFTP), Username, and Password in the top header, then click **Connect**.
3. **Select Local Path:** Click **Open Folder** on the left panel to choose the local directory you want to work from. Double-click folders to navigate.
4. **Select Remote Path:** Use the right panel to navigate to your target deployment folder on the server.
5. **Start Syncing:** Click **Auto Deploy**. The app will now watch your local folder. Any files you edit, rename, or delete locally will be automatically updated on the remote server.
6. Click **Stop Deploy** before disconnecting or closing the application.

## ⚠️ Important Considerations & Limitations

Mini Deploy is designed as a raw, one-way deployment pipeline. Because it actively modifies remote files, please be aware of the following:

* **One-Way Destructive Deployment:** The pipeline is strictly one-way (Local -> Remote). Modifying a local file will instantly overwrite the remote file of the same name without asking for confirmation or checking the remote file's timestamp. Please ensure you have backups of your server data.
* **No Workspace Verification:** The app will allow you to deploy any local folder into any remote folder. It does not check if the remote folder is already being used for something else. Always double-check your "Remote Path" before clicking Auto Deploy.

## 📄 License

This project is open-source and available for personal or educational use.