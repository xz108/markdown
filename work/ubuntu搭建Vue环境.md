ubuntu18.4 搭建Vue开发环境,创建Vue项目
1.环境搭建
1.1安装nodejs
sudo apt install nodejs

#查看是否安装成功,成功会有版本号输出
nodejs -v
1
2
3
4
1.2安装npm
sudo apt install npm

#查看是否安装成功,成功会有版本号输出
npm -v
1
2
3
4
1.3安装淘宝NPM镜像cnpm,为安装扩展提升速度
#时间较长，耐心等待
sudo npm install -g cnpm --registry=https://registry.npm.taobao.org

#查看是否安装成功,成功会有版本号输出
cnpm -v  
1
2
3
4
5
1.4安装vue脚手架工具vue-cli
sudo cnpm install -g vue-cli

#查看是否安装成功,成功会有版本号输出
vue -V
1
2
3
4
2.创建Vue项目
2.1创建基于webpack的项目,项目名为 first_vue
sudo vue init webpack first_vue
1
2.2安装依赖包
#进入目录
cd first_vue

#开始安装
sudo cnpm install
1
2
3
4
5
2.3运行项目,运行完成终端会出现项目访问链接（http://localhost:8080）在浏览器打开
sudo npm run dev 