# Configure Apache Password Authentication

![](../../.gitbook/assets/image%20%28108%29.png)

##  **步驟一、產生htpasswd**

### 透過htpasswd來產生

首先要安裝apache2-utils才能使用htpasswd

```text
sudo apt-get install apache2-utils 
```

接著輸入以下指令產生htpasswd \(其中/etc/httpd/conf/.webaccess為檔案產生位置 username001為使用者名稱\)  \(也可以在其他位置, e.g. /etc/apache2/.htpasswd\)

```text
sudo htpasswd -c /etc/httpd/conf/.webaccess username001
```

接著會提示需要輸入密碼 輸入兩次密碼後 會把檔案產生到指定的位置

假如要新增其他使用者則是輸入以下指令\(為前面的指令去掉-c\)

```text
sudo htpasswd /etc/httpd/conf/.webaccess username002
```

##  **步驟二、設定Apache來加上密碼驗證**

找出Apache virtual host設定檔位置, e.g. /etc/httpd/conf/httpd.conf

```text
# TICKETING ADMIN
Alias /ticketingadmin "/home/PROJECTS/ticketingadmin"
<Directory "/home/PROJECTS/ticketingadmin">
    Options MultiViews FollowSymLinks
    AllowOverride All
#   Order allow,deny
#   Allow from all
#   Require all granted
    AuthType Basic
    AuthName "Please enter your username and password"
    AuthUserFile "/etc/httpd/conf/.webaccess"
    <RequireAny>
      Require ip 192.168.110 20.10.1 127.0.0.1 192.168.111.200
      Require host localhost LTPRAP01
      Require valid-user
    </RequireAny>
</Directory>

```



























