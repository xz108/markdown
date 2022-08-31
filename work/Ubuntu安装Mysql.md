# Ubuntu安装Mysql  
1\使用apt命令安装

打开终端执行 ”sudo apt-get install mysql-server“ 即可。  

MySQL初始配置

在成功安装mysql后，可以直接使用root账户登录，注意这个账户是默认没有密码的。因此为了数据库的安全，需要第一时间给root用户设置密码。  
`GRANT ALL PRIVILEGES ON *.* TO root@localhost IDENTIFIED BY "<password>";
`  
将以上命令中的<password>替换为你要设定的密码即可。设置密码后，如果再以root用户登录就需要输入密码了，如：  
  
  建立数据库独立用户

root用户拥有数据库的所有操作权限，因此不能轻易给别人用。在一个MySQL实例中，我们可以创建多个数据库，而这些数据库可能会分属不同的项目，那么每个数据库的操作角色也就不一样。对此，我们可以针对不同的数据库，去指定用户进行访问。  
`create database db_web_monitor然后将这个数据库授予一个叫xavier的用户使用mysql> GRANT ALL PRIVILEGES ON db_web_monitor.* TO xavier@localhost IDENTIFIED BY "xavier";`
      
   GRANT ALL PRIVILEGES ON *.* TO 'xiaoxu'@'%' IDENTIFIED BY 'xiaoxu' WITH GRANT OPTION;
参数说明：第一个xiaoxu表示用户名，%表示所有的电脑都可以连接，也可以设置某个ip地址运行连接，第二个xiaoxu表示密码


  开放远程登录权限

1. 首先修改MySQL的配置文件，允许监听远程登录。  
2. 一、修改/etc/mysql/my.conf中指向的其他cnf文件
找到bind-address = 127.0.0.1这一行
改为bind-address = 0.0.0.0即可
3. `mysql>GRANT ALL PRIVILEGES ON db_web_monitor.* TO xavier@"%" IDENTIFIED BY "xavier";`
4. `mysql>GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'Myroot123';`

第三步：执行如下命令，立即生效

flush privileges;
roota
Myroot_123

第四步：查询数据库的用户，看看是否成功创建新用户，运行如下命令
````
SELECT DISTINCT CONCAT('User: ''',user,'''@''',host,''';') AS query FROM mysql.user;
````
打开3306端口，命令如下： 
sudo ufw allow 3306 