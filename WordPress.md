You can get the root dir of the Wordpress CMS by accessing the Server's config files:
[[nginx]]:
```bash
server {

	listen 80;
	listen [::]:80;

	root /var/www/metapress.htb/blog;

	index index
	....

```
or [[apache]] :
....
