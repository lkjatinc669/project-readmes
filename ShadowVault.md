# ShadowVault Backup System

## Overview
ShadowVault Backup System is a comprehensive solution for automating file backups from mobile devices to a server. It comprises three major components:

1. **ShadowVault Backup System** – The core script responsible for file transfer and management.
2. **ShadowVault Database** – A MongoDB-based multi-user database that maintains backup status and file metadata.
3. **ShadowVault HTTP API** – A FastAPI-based RESTful API for communication between the mobile client and the server.

## ShadowVault Backup System
The **ShadowVault Backup System** is a Python-based tool using `adb` (Android Debug Bridge) to manage file transfers between a mobile device and the server. It is responsible for:
- Identifying and fetching files from predefined directories on the mobile device.
- Transferring files securely to the designated server directories.
- Logging transfer statuses and maintaining metadata.

## ShadowVault Database System
A **MongoDB**-based system that supports multiple user roles:

1. **BackupModifier** – Updates the status of each transferred file from the mobile device to the server.
2. **APIUser** – Hosts and manages API request responses related to backup processes.
3. **Admin** – Has read-only access to monitor the system.
4. **BackupUser** – Manages file location configurations, additions, deletions, and modifications.
5. **DLUser** – Utilizes AI/ML to add metadata and label image files for classification.

## ShadowVault HTTP API
The **ShadowVault HTTP API**, built using FastAPI, enables seamless communication between the mobile client and the server. It supports:

1. **System Status Check** – The mobile client verifies if the server is online.
2. **Backup Availability Check** – The client queries the server for backup readiness.
3. **File Listing** – The server provides a list of files available for backup.
4. **File Transfer Initiation** – The client initiates the backup process by selecting files.
5. **Progress Monitoring** – The client receives status updates during file transfer.

## ShadowVault Important Directories
The system categorizes files based on source directories:

| Mobile Directory | Function | PC Directory |
|------------------|----------|--------------|
| DCIM/Camera | Stores camera images and videos | Camera-Images & Camera-Videos |
| Pictures/Screenshots | Stores screenshots | Screenshots |
| MIUI/sound_recorder | Stores system-recorded audio files | Phone-Recordings |
| MIUI/Shareme | Stores files shared via ShareMe | ShareMe Files |
| Downloads | Stores downloaded files | Download/{images, videos, text, pdfs, apks, isos, documents, etc.} |
| android/media/com.whatsapp/WhatsApp | Stores WhatsApp media files | WhatsApp/{all folders} |
| Pictures/Picsart | Stores Picsart-edited images | Picsart |
| Unknown images | Stores unrecognized image files | Uncategorized-Images |
| Unknown videos | Stores unrecognized video files | Uncategorized-Videos |

## ShadowVault Client – Mobile Application
The mobile client plays a crucial role in managing backups. It is responsible for:

1. A backup now button - A button that will start up the backing up process
2. A backup schedule - A feature that allows users to schedule backups at specific times
3. A backup history - A feature that allows users to view the history of backups
4. A backup status - A feature that allows users to view the status of the backup process
5. A backup settings - A feature that allows users to configure backup settings such as the frequency of backups and the directories to backup
6. Setting up a custom name for the directories

### Setttings page
1. Dark Mode / Light Mode
1. if location change then : { move / copy }
1. 

### how app will create all the data

On Scan There will be a two table 

Table 1:  `scan_data_folders`
| id | folder_name | folder_path | extensions of file |
|----|-------------|-------------|-------------------|
| 1  | DCIM        | /sdcard/DCIM | image, video, audio, text, pdf |

Table 2 : `scan_data_files`
| id | file_name | file_path | file_extension | is_changed | old_file_path |
|----|-----------|-----------|-----------------| ----- | ---- |
| 1  | image1.jpg | /sdcard/DCIM/image1.jpg | image | null | null |
| 2  | video1.mp4 | /sdcard/DCIM/video1.mp4 | video | null | null |

```

db = DB(scan_data_files)
sc = Scan(full_directory)

if db.exist(file_name):
    db.file_path = db.get_file_path(file_name)
    if db.file_path != sc.scanned_path:
        set db.is_changed = true
        set db.old_file_path = file_path
        set db.file_path = sc.scanned_path
```

The ShadowVault system is designed to provide a comprehensive backup solution for mobile devices, ensuring that users can easily manage and restore their files. The system's modular design and use of open-source technologies make it highly customizable and scalable. By leveraging AI/ML for image classification, the system can provide users with a more organized and structured backup experience. Overall, the ShadowVault system is a robust and feature-rich solution for mobile backup and management.

## Future Enhancements
- **Automated Scheduling** – Implement scheduled automatic backups.
- **Encrypted Transfers** – Secure file transfers using end-to-end encryption.
- **Cloud Integration** – Add support for backing up files to cloud storage providers.
- **AI-based File Classification** – Improve metadata labeling using machine learning.

This system provides a structured and efficient way to back up mobile files while ensuring flexibility and reliability.

