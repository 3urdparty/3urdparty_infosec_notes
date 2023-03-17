A proces can be in the following states:
- **Running** (waiting for an event or system resource)
- **Waiting**
- **Stopped**
- **Zombie** (stopped but still has an entry in the process table)

Check for running processes
```bash
ps -aux
```

They can be controlled using `kill`, `pkil`, `pgrep`, `killall`