## Task scheduling
To set up the cron daemon, we store the tasks in the `crontab` file. It consists of the following components

| Time frame             | Description                                                          |
| ---------------------- | -------------------------------------------------------------------- |
| Minutes (0-59)         | This speciied in which the minute task should be executed            |
| Hours (0-23)           | This specified in which hour the task shoudl be executed.            |
| Days of month (1-31)   | This speciied on which day of the month the task should be executed. |
| Months (1-12)          | This specified on which month the task should be executed.           |
| Days of the week (0-7) | This specified on which day of the week the task should be executed.                                                                     |

A `crontab` could look like:
```txt
# System Update
* */6 * * /path/to/update_software.sh

# Execute scripts
0 0 1 * * /path/to/scripts/run_scripts.sh

# Cleanup DB
0 0 * * 0 /path/to/scripts/clean_database.sh

# Backups
0 0 * * 7 /path/to/scripts/backup.sh
```
