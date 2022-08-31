## unable to access 'https://github.com/xz108/markdown.git/': Failed to connect to github.com port 443 after 21056 ms: Timed out
   
   1.多次尝试之后发现是代理问题，所以执行命令禁用代理配置即可（因为我使用的是https请求，所以取消https代理即可）

 

取消代理：
````
//取消http代理
git config --global --unset http.proxy
//取消https代理 
git config --global --unset https.proxy