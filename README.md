# wordpress

# Set 1：Download the latest version of WordPress

wget http://wordpress.org/latest.tar.gz

输入下面的内容来解压下载的存档

tar -xzvf latest.tar.gz

# Set 2：Create a database and users

为了让wordpress工作，现在需要同时建立一个数据库和一个用户，输入以下内容

mysql -u root -p

输入之前设置MySQL的密码，有可能怎么输都报错，此时重启MySQL，再输入前面的代码

创建一个新的数据库

CREATE DATABASE wordpress;

创建一个具有名称的用户，先输入用户名@locahost

 CREATE USER user@localhost;
 
 给用户的密码，可以根据自己的意愿输入新密码
 
 SET PASSWORD FOR user@localhost= PASSWORD("password");
 
 将所有特权授予用户
 
 GRANT ALL PRIVILEGES ON wordpress.* TO user@localhost IDENTIFIED BY 'password';
 
 刷新mysql
 
 FLUSH PRIVILEGES;
 
 最后输入exit完成退出
 
 exit
 
 下面是在控制台的外观
 
mysql> CREATE DATABASE wordpress;

Query OK, 1 row affected (0.00 sec)

mysql> CREATE USER user@localhost;

Query OK, 0 rows affected (0.00 sec)

mysql> SET PASSWORD FOR user@localhost= PASSWORD("password");

Query OK, 0 rows affected (0.00 sec)

mysql> GRANT ALL PRIVILEGES ON wordpress.* TO user@localhost IDENTIFIED BY 'password';

Query OK, 0 rows affected (0.00 sec)

mysql> FLUSH PRIVILEGES;

Query OK, 0 rows affected (0.00 sec)

mysql> exit

# Set 3：Set WordPress

必须为wordpress创建一个新的配置文件，通过将wp-config-sample.php文件的内容复制到一个名为 wp-config.php的文件夹中来实现的

cp ~/wordpress/wp-config-sample.php ~/wordpress/wp-config.php

之后再vi文本编辑器中打开这个文件

vi ~/wordpress/wp-config.php

在这里输入所有信息，数据库名称、数据库用户名和数据库密码

// ** MySQL settings - You can get this info from your web host ** //

/** The name of the database for WordPress */

define('DB_NAME', 'wordpress');

/** MySQL database username */

define('DB_USER', 'user');

/** MySQL database password */

define('DB_PASSWORD', 'password');

/** MySQL hostname */

define('DB_HOST', 'localhost');

完成更改后，关闭vi，按Esc，然后输入：wq！按Enter

# Set 4：Transfer Wordpres files to /var/www/html

下面的命令将完成从~/wordpress到/var/www/html所有内容的复制

cp -r ~/wordpress/* /var/www/html

重新启动web服务器

service httpd restart

# Step 5: Install WordPress on CentOS server

输入你的服务器的IP地址，在互联网中输入你的基本信息
