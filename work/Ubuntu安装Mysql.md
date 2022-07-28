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
  
  开放远程登录权限

1. 首先修改MySQL的配置文件，允许监听远程登录。  
2. `mysql>GRANT ALL PRIVILEGES ON db_web_monitor.* TO xavier@"%" IDENTIFIED BY "xavier";`