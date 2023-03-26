# Commands
```
Usage: passpie [OPTIONS] COMMAND [ARGS]...

Options:
  -D, --database TEXT  Database path or url to remote repository
  --autopull TEXT      Autopull changes from remote pository
  --autopush TEXT      Autopush changes to remote pository
  --config PATH        Path to configuration file
  -v, --verbose        Activate verbose output
  --version            Show the version and exit.
  --help               Show this message and exit.

Commands:
  add       Add new credential to database
  complete  Generate completion scripts for shells
  config    Show current configuration for shell
  copy      Copy credential password to clipboard/stdout
  export    Export credentials in plain text
  import    Import credentials from path
  init      Initialize new passpie database
  list      Print credential as a table
  log       Shows passpie database changes history
  purge     Remove all credentials from database
  remove    Remove credential
  reset     Renew passpie database and re-encrypt...
  search    Search credentials by regular expressions
  status    Diagnose database for improvements
  update    Update credential

```

Command line password manager. using GnuPG and saved into yaml text files. Passpie supports Linux, OSX and Windows.
List all stored passwords:
```bash
> passpie list
```
Export passwords to a file using:
```bash
> passpie export file_name
```