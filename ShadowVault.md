# ShadowVaultBackupSystem

## How it works?

The whole system works on three major components
    - ShadowVault Backup System
    - ShadowVault Database
    - ShadowVault HTTP API

The ShadowVaultBackupSystem is a Python script that automates the process of backing up files from a specified source directory to a destination directory. It uses the `shutil` module to copy files and 

## ShadowVault Backup System
A system made with `python-abd` which will manage the task of pulling the files
 
## ShadowVault Database System
A mongodb database system multi-user 
1. **BackupModifier**: A user backupModifer that will update the status of the transfered file as soon as the each file is transferred to the phone system to the server system
2. **APIUser** : A user APIUser that will host the status of the updates
3. **Admin**: A admin which can only view the system
4. **BackupUser**: A user that will maintain addition-deletion and modification of files locations from where it fetched and deleted
4. **DLUser**: A DL/ML/AI user that will add the metadata and work of labelling the images

## ShadowVault HTTP API
A api made in python using `fastapi` which will allow the followings things

1. A mobile client will check if there is any api on the system
1. The mobile client will ask if the system is up and availble for backup process
2. The server will ask for a list of files available
3. The client will respond with all the important directories and system files



## ShadowVault Important listing directories

| Mobile Directory | Function | PC Directory |
| ----- | ----- | ----- |
| DCIM/Camera | All the camera images are stored here | Camera-Images & Camera-Videos |
| Pictures/Screenshots | All the  | s |
| MIUI/sound_recorder | All the system recorded files are stored here  | All the phone recorded things will be shown here |
| MIUI/Shareme | All the ShareMe shared items are shorted here | Shareme files |
| Downloads | All the downloaded files will be stored here | Download/{extension(images, videos, text, pdfs, apks, isos, microsofts, others)} | 
| android/media/com.whatsapp/Whatsapp or Whatsapp/ | All the whatsapp logo | Whatsapp/{all folders} |
| Pictures/Picsart | Picsart Images | Picsart |
| Unknown images | If images found | path.join("-") - images |
| Unknown videos | If videos found | path.join("-") - videos |


## ShadowVault Client : A mobile application responsible for managing backup

1. Managing directories: The client will manage help the server to identify the directories and files to be backed up
2. File selection: The client will select the files to be backed up
3. Backup process: The client will initiate the backup process and monitor its progress
4. File transfer: The client will transfer the selected files to the server
5. File verification: The client will verify the integrity of the transferred files