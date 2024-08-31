apt install aria2 apache2

mkdir /etc/aria2c

cp ./aria2c.conf /etc/aria2c/
cp ./aria2c.session /etc/aria2c/

mkdir /var/www/ariang
cp ./index.html /var/www/ariang

vim /etc/apache2/sites-enabled/ariang.conf
```
Alias /ariang "/var/www/ariang/"

<Directory /var/www/ariang/>
  Require all granted
  AllowOverride All
  Options FollowSymLinks MultiViews

  <IfModule mod_dav.c>
    Dav off
  </IfModule>
</Directory>
```

cp ./aria2c.service /etc/systemd/system/
systemctl enable aria2c
systemctl start aria2c
