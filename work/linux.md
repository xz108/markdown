## Linux命令
1. ls
2. ll
3. 查看linux内核版本 ` uname -r `
4. cat df 查看查看硬盘剩余空间
5. sudo apt-get install sysstat安装 
6. 更新`sudo apt-get update
`
6. 安装docker
   `curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun` 
<br>docker -v
<br>docker pull redis
<br>以下命令使用 ubuntu 镜像启动一个容器，参数为以命令行模式进入该容器：
`docker run -it redis /bin/bash 
docker run -p 6379:6379 -d redis:latest redis-server`

<br>
<br>查看所有的容器命令如下：
<br>`docker ps -a`
<br>使用 docker start 启动一个已停止的容器：
<br>docker start b750bbbcfd88 
<br>在大部分的场景下，我们希望 docker 的服务是在后台运行的，我们可以过 -d 指定容器的运行模式。
`docker run -itd --name ubuntu-test ubuntu /bin/bash`
<br>停止容器的命令如下：
` docker stop <容器 ID>`
<br>进入容器
exec 命令

  下面演示了使用 docker exec 命令。
  `docker exec -it 243c32535da7 /bin/bash`
  `docker exec -ti d0b86 redis-cli`


1. 启动docker
service docker start
 

2. 设置开机启动docker
systemctl enable docker


3. 停止docker
systemctl stop docker
C:\Users\admin\.vscode\work\linux.md