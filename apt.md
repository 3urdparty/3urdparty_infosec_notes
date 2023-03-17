- For Debian-based linux distros
- Package is an archive file containing `.deb` files
- Repos can be labled as **stable**, **testing** or **unstable**


`/etc/apt/sources.list` - Sources

**APT** uses a db called **APT Cache**:

This can be used to search for packages related to search query.
```bash
apt-cache search impacket
```

List all installed packages:
```bash
apt list --installed
```
