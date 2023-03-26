Secure copy  is a command-line utility that allows you to securely copy files and directories between two locations.

## Usage
```bash
scp [OPTION] [user@]SRC_HOST:]file1 [user@]DEST_HOST:]file2
```

OPTION - scp options such as cipher, ssh configuration, ssh port, limit, recursive copy …etc.
[user@]SRC_HOST:]file1 - Source file.
[user@]DEST_HOST:]file2 - Destination file

scp provides a number of options that control every aspect of its behavior. The most widely used options are:

    -P - Specifies the remote host ssh port.
    -p - Preserves files modification and access times.
    -q - Use this option if you want to suppress the progress meter and non-error messages.
    -C - This option forces scp to compresses the data as it is sent to the destination machine.
    -r - This option tells scp to copy directories recursively.
    
You can use `scp` to transmit files over [[ssh]]:
```bash
scp jnelson@10.10.11.186:.passpie/.keys .keys
```
