# Auto Deploy

Mini Deploy is a lightweight, GUI-based Python application designed for real-time file synchronization over SFTP. It allows you to connect to a remote server, browse local and remote directories side-by-side, and automatically deploy changes (saves, renames, and deletions) from your local machine to the server using a background observer.

## Features

* **Simple GUI Interface:** Built with Tkinter for an easy-to-use, split-pane file browsing experience.
* **SFTP Protocol:** Securely transfers files using Paramiko.
* **Real-Time Auto-Deploy:** Utilizes Watchdog to monitor a selected local directory. Any file modifications, renames, or deletions are instantly mirrored to the remote server.
* **Activity Logging:** An embedded log console tracks all connection statuses, file uploads, and errors.

## Prerequisites

To run this application, you will need **Python 3.x** installed on your system along with a few external libraries. 

You can install the required dependencies using your terminal:

    pip install paramiko watchdog

*(Note: `tkinter` is included in the standard Python library, but on some Linux distributions, you may need to install it separately via your package manager, e.g., `sudo apt-get install python3-tk`).*

## Usage

1. Run the script from your terminal:
    
    python deploy_window.py

2. **Connect to Server:** Enter your server's IP, Port (usually 22 for SFTP), Username, and Password in the top header, then click **Connect**.
3. **Select Local Path:** Click **Open Folder** on the left panel to choose the local directory you want to work from. Double-click folders to navigate.
4. **Select Remote Path:** Use the right panel to navigate to your target deployment folder on the server.
5. **Start Syncing:** Click **Auto Deploy**. The app will now watch your local folder. Any files you edit, rename, or delete locally will be automatically updated on the remote server.
6. Click **Stop Deploy** before disconnecting or closing the application.

## Important Considerations & Known Limitations

Mini Deploy is a powerful automation tool, but because it actively modifies remote files, please be aware of the following current limitations:

* **One-Way Destructive Sync:** The sync is strictly one-way (Local -> Remote). Modifying a local file will instantly overwrite the remote file of the same name without confirmation. Please ensure you have backups of your server data.
* **Folder Creation:** Currently, the auto-deploy observer handles file modifications, renames, and deletions. Creating entirely new directories locally *after* starting the deployment may throw an upload error until the folder is manually created on the remote server.
* **Host Key Verification:** The current connection method bypasses strict SSH host key verification. Avoid using this tool on untrusted public networks to prevent Man-in-the-Middle (MITM) interceptions.
* **UI Responsiveness:** Large file transfers or slow server responses may temporarily pause the UI thread while the upload completes.

## License

This project is open-source and available for personal or educational use.