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