Open-source tool that allows us to quickly and securely back up files and folders to a remote location.

To install:
```bash
sudo apt install rsync -y
```

Backup a local directory to our Backup-Server:
```bash
rsync -av /path/to/mydirectory user@backup_server:/path/to/backup/directory
```

Options including using compression and incremental backups:
```bash
rsync -avz --backup --backup-dir=/path/to/backup/folder --delete /path/to/mydirectory user@backup_server:/path/to/backup/directory
```

This backs up `mydirectory` to the remote `backup_server`.

To restore our back up:
```bash
rsync -av user@remote_host:/path/to/backup/directory /path/to/mydirectory
```

## Auto-synchronization
To enable auto-synchronization using `rsync` you can use `cron` and `rsync`. To do so we create a new script called `RSYNC_Backup.sh`:

```bash
#!/bin/bash
rsync -avz -e ssh /path/to/mydirectory user@backup_server:/path/to/backup/dir
```

Then we use [[chmod]] to adjust permissions:
```bash
chmod +x RSYNC_Backup.sh
```

Then we create a crontab that tells [[Cron]] to run the script:
```
0 * * * * /path/to/RSYNC_Backup.sh
```