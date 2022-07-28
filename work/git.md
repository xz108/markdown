## git报错: OpenSSL SSL_read: Connection was reset, errno 10054

1. 产生原因：一般是这是因为服务器的SSL证书没有经过第三方机构的签署，所以才报错
参考网上的解决方法：输入 **

git config --global http.sslVerify "false"

## git 配置
1. 4.Git配置
这里的配置方式gitee和github都是类似的。

（1）用户名和邮箱
安装Git后首先要做的事情是设置你的用户名称和e-mail地址。这是非常重要的，因为每次Git提交都会使用该信息。
git config --global user.name "your name"
git config --global user.email "email@qq.com"
只需要做一次这个设置，如果你传递了–global 选项，因为Git将总是会使用该信息来处理你在系统中所做的一切操作。如果你希望在一个特定的项目中使用不同的名称或e-mail地址，你可以在该项目中运行该命令而不要–global选项。总之–global为全局配置，不加为某个项目的特定配置。 