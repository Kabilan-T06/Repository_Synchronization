# SFTP Directory Synchronization Tool

This Python script synchronizes files between a local directory and a remote SFTP server. It ensures that any changes in the local directory (creation, modification, deletion, or movement of files) are reflected in the remote directory and vice versa.

## Features
- Automatically syncs local files to the remote server if they are newer.
- Automatically syncs remote files to the local machine if they are newer.
- Uses `watchdog` to detect file changes in real-time.
- Recursively syncs directories in both directions.

## Requirements
- Python 3.x
- `paramiko` for SFTP communication
- `watchdog` for file system event monitoring

## Installation
Install the required dependencies using pip:
```bash
pip install paramiko watchdog
```

## Usage
1. Update the script with your SFTP server details:
    ```python
    hostname = "your.sftp.server"
    port = 22
    username = "your_username"
    password = "your_password"

    local_directory = "path/to/local/directory"
    remote_directory = "/path/to/remote/directory"
    ```
2. Run the script:
    ```bash
    python sync_script.py
    ```

## How It Works
- The script establishes an SFTP connection to the remote server.
- It continuously monitors the local directory for any file changes.
- If a file is modified or created, it is uploaded to the remote directory.
- If a file is deleted locally, it is removed from the remote directory.
- The script also checks for updates on the remote server and downloads any modified files.

## Handling Events
The script listens for file system events using `watchdog` and triggers the following actions:
- **File modified** → Sync the updated file.
- **File created** → Upload the new file.
- **File deleted** → Remove it from the remote directory.
- **File moved** → Update its location accordingly.

## Stopping the Script
To stop the script, press `CTRL + C` in the terminal.

## License
This project is open-source and available under the MIT License
