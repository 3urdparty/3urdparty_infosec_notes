# Installation
```bash
sudo apt install apache2 -y
```
We can edit the file `/etc/apache2/apache2.conf` to configure settings like which folders can be accessed

```txt
<Directory /var/www/html>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</directory>
```
This section specified that the default `/var/ww/html` folder is accessiblem that users can use the `Indexes` and `FollowSymLinks` options, `AllowOverride All`, and `Require all granted` grants all users access to this directory.

To customize individual settings at directory level by using the `.htaccess` file which we can create in the directory in question.
