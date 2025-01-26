---
weight: 620
title: "Pterodactyl"
description: "Open-source game server management panel built with PHP, React, and Go."
icon: "api"
date: "2024-03-16T22:53:27+01:00"
lastmod: "2024-03-16T22:53:27+01:00"
draft: false
toc: true
---

### Picking a Server OS

{{< table "table-striped table-hover" >}}
| Operating System  | Version | Supported | Notes  |
|---------|--------|-----|--------|
| `Ubuntu` |  22.04 | ✅ | Documentation written assuming Ubuntu 20.04 as the base OS. |
|        |  22.04 | ✅ | MariaDB can be installed without the repo setup script. |
| `CentOS` | 7 | ✅ | Extra repos are required. |
|        | 8 | ✅ | Note that CentOS 8 is EOL. Use Rocky or Alma Linux. |
| `Debian` | 11 | ✅ |  |
| `Debian` | 12 | ✅ |  |
{{< /table >}}

### Dependency Installation

```sh
# Add "add-apt-repository" command
apt -y install software-properties-common curl apt-transport-https ca-certificates gnupg

# Add additional repositories for PHP, Redis, and MariaDB
LC_ALL=C.UTF-8 add-apt-repository -y ppa:ondrej/php

# Add Redis official APT repository
curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list

# MariaDB repo setup script can be skipped on Ubuntu 22.04
curl -sS https://downloads.mariadb.com/MariaDB/mariadb_repo_setup | sudo bash

# Update repositories list
apt update

# Install Dependencies
apt -y install php8.1 php8.1-{common,cli,gd,mysql,mbstring,bcmath,xml,fpm,curl,zip} mariadb-server nginx tar unzip git redis-server
```
### Installing Composer

```sh
curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer
```

### Download Files

```sh
mkdir -p /var/www/pterodactyl
cd /var/www/pterodactyl
```

```sh
curl -Lo panel.tar.gz https://github.com/pterodactyl/panel/releases/latest/download/panel.tar.gz
tar -xzvf panel.tar.gz
chmod -R 755 storage/* bootstrap/cache/
```

###  Installation

{{% alert icon="🛢 " context="success" %}}
#### Setting up MySQL
You will need a database setup and a user with the correct permissions created for that database before continuing any further.
{{% /alert %}}

##### Logging In
```sh
mysql -u root -p
```
##### Creating a user

```sql
# Remember to change 'somePassword' below to be a unique password specific to this account.
CREATE USER 'pterodactyl'@'127.0.0.1' IDENTIFIED BY 'somePassword';
```
##### Create a database

```sql
CREATE DATABASE panel;
```

#####  Assigning permissions

```sql
GRANT ALL PRIVILEGES ON panel.* TO 'pterodactyl'@'127.0.0.1';
```

##### Allowing external database access

To allow external access to this MySQL instance in order to allow servers to connect to it you'll need to edit `my.cnf`.\
You can type `find /etc -iname my.cnf` to locate it.

```sh
find /etc -iname my.cnf
cd /etc/mysql/            #in my case
nano my.cnf
```
Add text below to the bottom of the file and save it

```conf
[mysqld]
bind-address=0.0.0.0
```

```sh
cp .env.example .env
composer install --no-dev --optimize-autoloader

# Only run the command below if you are installing this Panel for
# the first time and do not have any Pterodactyl Panel data in the database.
php artisan key:generate --force
```

##### Environment Configuration

```sh
php artisan p:environment:setup
```

* Enter: `email`, `https://urwebsite.exaple`, `timezone` and **press 4 times enter**

```sh
php artisan p:environment:database

# To use PHP's internal mail sending (not recommended), select "mail". To use a
# custom SMTP server, select "smtp".
# php artisan p:environment:mail
```
* Press 4 times enter + `somepassword`

### Database Setup 

```sh
php artisan migrate --seed --force
```

```sh
php artisan p:user:make
```

* Enter: Yes, email, username, first name, last name and password.

### Set Permissions

```sh
# If using NGINX or Apache (not on CentOS):
chown -R www-data:www-data /var/www/pterodactyl/*

# If using NGINX on CentOS:
chown -R nginx:nginx /var/www/pterodactyl/*

# If using Apache on CentOS
chown -R apache:apache /var/www/pterodactyl/*
```

### Crontab Configuration 

```sh
sudo crontab -e
1
* * * * * php /var/www/pterodactyl/artisan schedule:run >> /dev/null 2>&1
```

### Create Queue Worker

Create a file called `pteroq.service` in `/etc/systemd/system` with the contents below.

```conf
# Pterodactyl Queue Worker File
# ----------------------------------

[Unit]
Description=Pterodactyl Queue Worker
After=redis-server.service

[Service]
# On some systems the user and group might be different.
# Some systems use `apache` or `nginx` as the user and group.
User=www-data
Group=www-data
Restart=always
ExecStart=/usr/bin/php /var/www/pterodactyl/artisan queue:work --queue=high,standard,low --sleep=3 --tries=3
StartLimitInterval=180
StartLimitBurst=30
RestartSec=5s

[Install]
WantedBy=multi-user.target
```
```sh
sudo systemctl enable --now redis-server
```

```sh
sudo systemctl enable --now pteroq.service
```

### Webserver Configuration

{{< alert context="warning" text="When using the SSL configuration you MUST create SSL certificates, otherwise your webserver will fail to start." />}}


{{< tabs tabTotal="2">}}
{{< tab tabName="NGINX With SSL" >}}

&nbsp;

{{< markdownify >}}
> ###### First, remove the default NGINX configuration.
{{< /markdownify >}}

{{< prism lang="sh" >}}
rm /etc/nginx/sites-enabled/default
{{< /prism >}}

{{< markdownify >}}
> ###### Make file called `pterodactyl.conf` and place the file in `/etc/nginx/sites-available/`, or — if on CentOS, `/etc/nginx/conf.d/`
{{< /markdownify >}}

{{< prism lang="sh" >}}
cd /etc/nginx/sites-available/
nano pterodactyl.conf
{{< /prism >}}

{{< prism lang="conf" line-numbers="true" line="5,11,26-27" >}}
server_tokens off;

server {
    listen 80;
    server_name <domain>;
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl http2;
    server_name <domain>;

    root /var/www/pterodactyl/public;
    index index.php;

    access_log /var/log/nginx/pterodactyl.app-access.log;
    error_log  /var/log/nginx/pterodactyl.app-error.log error;

    # allow larger file uploads and longer script runtimes
    client_max_body_size 100m;
    client_body_timeout 120s;

    sendfile off;

    # SSL Configuration - Replace the example <domain> with your domain
    ssl_certificate /etc/letsencrypt/live/<domain>/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/<domain>/privkey.pem;
    ssl_session_cache shared:SSL:10m;
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers "ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384";
    ssl_prefer_server_ciphers on;

    # See https://hstspreload.org/ before uncommenting the line below.
    # add_header Strict-Transport-Security "max-age=15768000; preload;";
    add_header X-Content-Type-Options nosniff;
    add_header X-XSS-Protection "1; mode=block";
    add_header X-Robots-Tag none;
    add_header Content-Security-Policy "frame-ancestors 'self'";
    add_header X-Frame-Options DENY;
    add_header Referrer-Policy same-origin;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_pass unix:/run/php/php8.1-fpm.sock;
        fastcgi_index index.php;
        include fastcgi_params;
        fastcgi_param PHP_VALUE "upload_max_filesize = 100M \n post_max_size=100M";
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        fastcgi_param HTTP_PROXY "";
        fastcgi_intercept_errors off;
        fastcgi_buffer_size 16k;
        fastcgi_buffers 4 16k;
        fastcgi_connect_timeout 300;
        fastcgi_send_timeout 300;
        fastcgi_read_timeout 300;
        include /etc/nginx/fastcgi_params;
    }

    location ~ /\.ht {
        deny all;
    }
}
{{< /prism >}}

{{< markdownify >}}
##### Enabling Configuration
{{< /markdownify >}}

{{< markdownify >}}
```sh
# You do not need to symlink this file if you are using CentOS.
sudo ln -s /etc/nginx/sites-available/pterodactyl.conf /etc/nginx/sites-enabled/pterodactyl.conf

# You need to restart nginx regardless of OS.
sudo systemctl restart nginx
```
{{< /markdownify >}}


{{< /tab >}}
{{< tab tabName="Apache With SSL" >}}

&nbsp;

{{< markdownify >}}
> ###### First, remove the default Apache configuration.
{{< /markdownify >}}

{{< prism lang="sh" >}}
a2dissite 000-default.conf
{{< /prism >}}

{{< markdownify >}}
> ###### Make file called `pterodactyl.conf` and place the file in `/etc/apache2/sites-available`, or — if on CentOS, `/etc/httpd/conf.d/`
{{< /markdownify >}}

{{< prism lang="sh" >}}
cd /etc/apache2/sites-available
nano pterodactyl.conf
{{< /prism >}}

{{< prism lang="conf" line="2,10,24-25" >}}
<VirtualHost *:80>
  ServerName <domain>
  
  RewriteEngine On
  RewriteCond %{HTTPS} !=on
  RewriteRule ^/?(.*) https://%{SERVER_NAME}/$1 [R,L] 
</VirtualHost>

<VirtualHost *:443>
  ServerName <domain>
  DocumentRoot "/var/www/pterodactyl/public"

  AllowEncodedSlashes On
  
  php_value upload_max_filesize 100M
  php_value post_max_size 100M

  <Directory "/var/www/pterodactyl/public">
    Require all granted
    AllowOverride all
  </Directory>

  SSLEngine on
  SSLCertificateFile /etc/letsencrypt/live/<domain>/fullchain.pem
  SSLCertificateKeyFile /etc/letsencrypt/live/<domain>/privkey.pem
</VirtualHost> 
{{< /prism >}}

{{< markdownify >}}
##### Enabling Configuration
{{< /markdownify >}}

{{< markdownify >}}
> ###### If you are on CentOS you do not need to run the commands below! You only need to run `systemctl restart httpd`
{{< /markdownify >}}


{{< markdownify >}}
```sh
# You do not need to run any of these commands on CentOS
sudo ln -s /etc/apache2/sites-available/pterodactyl.conf /etc/apache2/sites-enabled/pterodactyl.conf
sudo a2enmod rewrite
sudo a2enmod ssl
sudo systemctl restart apache2
```
{{< /markdownify >}}


{{< /tab >}}
{{< /tabs >}}

###  Installing Wings

{{< markdownify >}}
> ###### Wings is the next generation server control plane from Pterodactyl. It has been rebuilt from the ground up using Go and lessons learned from our first Nodejs Daemon.
{{< /markdownify >}}

{{< markdownify >}}
##### Installing Docker
{{< /markdownify >}}

{{< markdownify >}}
```sh
curl -sSL https://get.docker.com/ | CHANNEL=stable bash
```
{{< /markdownify >}}

{{< markdownify >}}
##### Start Docker on Boot
{{< /markdownify >}}

{{< markdownify >}}
```sh
sudo systemctl enable --now docker
```
{{< /markdownify >}}

{{< markdownify >}}
##### Enabling Swap
{{< /markdownify >}}

{{< markdownify >}}
> ###### To enable swap, open `/etc/default/grub` as a root user and find the line starting with `GRUB_CMDLINE_LINUX_DEFAULT`. Make sure the line includes `swapaccount=1` somewhere inside the double-quotes.
> ###### After that, run `sudo update-grub` followed by `sudo reboot` to restart the server and have swap enabled. 
{{< /markdownify >}}

{{< markdownify >}}
```conf
GRUB_CMDLINE_LINUX_DEFAULT="swapaccount=1"
```
{{< /markdownify >}}

{{< markdownify >}}
##### Installing Wings
{{< /markdownify >}}

{{< markdownify >}}
```sh
sudo mkdir -p /etc/pterodactyl
curl -L -o /usr/local/bin/wings "https://github.com/pterodactyl/wings/releases/latest/download/wings_linux_$([[ "$(uname -m)" == "x86_64" ]] && echo "amd64" || echo "arm64")"
sudo chmod u+x /usr/local/bin/wings
```
{{< /markdownify >}}

{{< markdownify >}}
##### Configure
{{< /markdownify >}}

{{< markdownify >}}
> ###### Once you have installed Wings and the required components, the next step is to create a node on your installed Panel. Go to your Panel administrative view, select Nodes from the sidebar, and on the right side click Create New button.
> ###### After you have created a node, click on it and there will be a tab called Configuration. Copy the code block content, paste it into a new file called `config.yml` in `/etc/pterodactyl` and save it.
> ###### `Alternatively, you can click on the Generate Token button, copy the bash command and paste it into your terminal`.
{{< /markdownify >}}

{{< alert context="warning" text="When your Panel is using SSL, the Wings must also have one created for its FQDN." />}}

{{< markdownify >}}
##### Starting Wings
{{< /markdownify >}}

{{< markdownify >}}
```sh
sudo wings
# You may optionally add the --debug flag to run Wings in debug mode.
```
{{< /markdownify >}}

{{< markdownify >}}
##### Daemonizing
{{< /markdownify >}}

{{< markdownify >}}
> ###### Place the contents below in a file called `wings.service` in the `/etc/systemd/system` directory.
{{< /markdownify >}}

{{< markdownify >}}
```conf
[Unit]
Description=Pterodactyl Wings Daemon
After=docker.service
Requires=docker.service
PartOf=docker.service

[Service]
User=root
WorkingDirectory=/etc/pterodactyl
LimitNOFILE=4096
PIDFile=/var/run/wings/daemon.pid
ExecStart=/usr/local/bin/wings
Restart=on-failure
StartLimitInterval=180
StartLimitBurst=30
RestartSec=5s

[Install]
WantedBy=multi-user.target
```
{{< /markdownify >}}

{{< markdownify >}}
> ###### Then, run the commands below to reload systemd and start Wings.
{{< /markdownify >}}

{{< markdownify >}}
```sh
systemctl enable --now wings
```
{{< /markdownify >}}

