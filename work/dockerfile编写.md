# dockerfile
## 流程
1. 手动编写一个dockerfile 文件 
2. docker build 执行 ，获得一个 自定义的镜像
3. run
## 保留字
1. FROM 基础镜像
2. RUN 执行的命令
3. MAINTAINER 维护人的姓名和邮箱
4. ENV 设置环境变量
5. EXPOSE 暴露的端口
6. WORKDIR 终端进入目录工作
7. ADD 拷贝并解压
8. COPY 将宿主机目录文件拷贝到镜像
9. VOLUME
10. CMD 只执行最后一个
11. ENTRYPOINT 类CMD 追加执行
12. ONBUILD 当构建被继承的Dockerfile运行，父镜像在被自镜像继承ONBUILD执行

  
  ## 例子
    FROM centos:7 #使用版本7，默认8不行
    MAINTAINER EERT1<1826715363@qq.com>
    ENV mypath /tmp
    WORKDIR $mypath
    RUN yum update -y
    RUN yum -y install vim
    RUN yum -y install net-tools

    EXPOSE 80
    CMD echo $mypath
    CMD /bin/bash
   小心from默认最新版本  

创建一个文件夹 docker里面放dockerfile
在目录执行
    
    docker build -t mycentos:1.0 .
    docker build -f /docker/dockerfile -t myip .

dockerfile 2
    
    FROM centos:7
    RUN yum install -y curl
    CMD ["curl","-s","http://ip.cn"]
dockerfile 3
    
    FROM centos:7
    RUN yum install -y curl
    ENTRYPOINT ["curl","-s","https://ip.cn"]

  

