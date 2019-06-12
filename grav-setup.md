# Setup & Running GravCMS on Linux
---

1. Install apache2 and php
```sh
sudo apt-get install apache2 php libapache2-mod-php
```

2. Move index.php to the front in
```sh
sudo nano /etc/apache2/mods-enabled/dir.conf
```

3. Install other php modules
```sh
sudo apt-get install php-cli php-curl php-gd php-json php-mbstring php-xml php-zip php-apcu php-yaml php-xdebug
```

4. Restart the apache server
```sh
sudo systemctl restart apache2
```

5. Enable mod_rewrite
```sh
sudo a2enmod rewrite
```

6. Append ServerName 127.0.0.1 in
```sh
sudo vim /etc/apache2/apache2.conf
```

7. This command should output "Syntax OK"
```sh
sudo apache2ctl configtest
```

8. To list the apache user
```sh
ps aux | grep -v root | grep apache | cut -d\  -f1 | sort | uniq
```
9. Add user **username** to group www-data
```sh
sudo usermod -a -G www-data username
```
10. Check **username**'s groups
```sh
groups username
```

11. Download [grav](https://getgrav.org/downloads) and extract it to the path
```sh
cd /var/www/html/
sudo unzip grav.zip
cd grav
```

12. Change the permissions to 644 and 755 for files and folders
```sh
sudo chgrp -R www-data .
find . -type f | sudo xargs chmod 664
find ./bin -type f | sudo xargs chmod 775
find . -type d | sudo xargs chmod 775
find . -type d | sudo xargs chmod +s
umask 0002
```

13. Just restart the server
```sh
sudo systemctl restart apache2
```

14. Open localhost/grav or 127.0.0.1/grav in the browser.

> In case the site redirect from http to https, change "force_ssl: true" to "force_ssl: false" in grav/user/config/system.yaml
