# Ubuntu 安装 jdk8
```
1、在 ubuntu 中  输入 uname -a 查看 ubuntu 的版本
2、在 ubuntu 中 新建 一个 jdk8 目录，（输入  mkdir jdk8 ）
3、将下载的 jdk8 传入 ubuntu的 jdk8 目录 中（  你可以通过 ftp 服务器 或者 Xftp 工具 方式） 

4、 tar -zxvf jdk-8u221-linux-x64.tar.gz 
5、配置环境变量 （ 输入  vim /etc/profile  进行编辑  ），在文件内容最后加入，注：vim 命令不能使用的，自个去安装个 vim 或者 使用 gedit 命令 ，没有权限的  在 前面 加  sudo 
```java
export JAVA_HOME=/root/java/jdk1.8.0_162
export JRE_HOME=${JAVA_HOME}/jre  
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib  
export PATH=${JAVA_HOME}/bin:$PATH
```
 7、让 配置文件 立即生效
 `source /etc/profile`