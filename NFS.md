Network File System (`NFS`) is a network protocol that allows us to store and manage files on remote systems as if they were stored on the local system.

NFS servers for Linux include:
- [[NFS-UTILS]] - for the `Ubuntu`
- [[NFS-Ganesha]] - for `Solaris`
- [[OpenNFS]] - for `Redhat Linux`

We can install NFS using:
```bash
sudo apt install nfs-kernel-server
```
Then check if server is running:
```bash
systemctl status nfs-kernel-server
```

We can configure NFS via the configuration file at `etc/exports`.
Access rights that can be configured in NFS:

| Permissions      | Description                                                                                                                                             |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `rw`             | Gives users and system read and write permission to the shared directory                                                                                |
| `ro`             | Gives users and systems read-only access to the shared directory                                                                                        |
| `no_root_squash` | Prevents teh root user on the client from being restricted to the rights of a normal user.                                                              |
| `root_squash`    | Restricts the rights of the root user on the client to the rights of a normal user.                                                                     |
| `sync`           | Synchrizes the transfer of data to ensure that changes are only transferred after they have been saved on the file system.                              |
| `async`          | Transfers data asynchronously, which makes the transer faster, but may cause inconsistencies in the file system if changes have not been fully commited |

### Create NFS share
```bash
mkdir nfs_sharing
echo '/home/cry0l1t3/nfs_sharing hostname(rw,sync,no_root_squash)' >> /etc/exports
cat /etc/exports | grep -v '#'
```

### Mount NFS Share
```bash
mkdir ~/target_nfs
mount 10.129.12.17:/home/john/dev_scripts ~/target_nfs
```
