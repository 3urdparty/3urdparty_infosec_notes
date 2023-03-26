`SysV` script - tells the system to run the service after startup.

To add to `SysV` use:
```bash
systemctl enable ssh
```

We can check for running processes using [[Processes]].
We can also list all services using `systemctl`
```bash
systemctl list-units --type=service
```

## journalctl
We can check the logs for an process using `journalctl

## Task automation
3 steps to automate scripts:
1. Create a timer
2. Create a service
3. Activate the timer

### 1. Create a Timer
First, create a directory where the timer script will be stored:
```bash
sudo mkdir /etc/systemd/system/mytimer.timer.d
sudo vim /etc/systemd/system/mytimer.timer
```
Script must contain `Unit`, `Timer`, `Install`.

The content of mytimer.timer:
```txt
[Unit]
Description=My Timer

[Timer]
OnBootSec=3min
OnUnitActiveSec=1hour

[Install]
WantedBy=timers.target
```

#### Options
##### Unit
##### Timer
- **OnBootSec** - run our script only once after the system boot
- **OnUnitActiveSec** - to have the system run the script at regular intervals.

##### Install
### 2. Create a service
To create a service:
```bash
sudo vim /etc/systemd/system/mytimer.service
```

Content of `mytimer.service`:
```txt
[Unit]
Description=My Service

[Service]
ExecStart=/full/path/to/my/script.sh

[Install]
WantedBy=multi-user.target
```

Then reload system:
```bash
sudo systemctl daemon-reload
```

Then enable the autostart using:
```bash
sudo systemctl start mytimer.service
sudo systemctl enable mytimer.service
```