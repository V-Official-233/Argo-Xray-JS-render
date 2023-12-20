# Argo-Xray-JS-render
使用奇妙的方法在render上部署fscarmen2的[Argo-Xray-JS-PaaS项目](https://github.com/fscarmen2/Argo-Xray-JS-PaaS)，请注意，本项目不能使用临时隧道！

默认使用的镜像为 Debian 如果你想缓存 Ubuntu Dockerfile 请填写 `./Ubuntu/Dockerfile`

请Fork此仓库部署，请不要直接使用此仓库部署！

Fork后在render引用你Fork后的仓库部署，部署完毕后（记得使用Uptimerobot或是别的ping平台来保活！）访问URL使用shell in a box登录，默认账密如下：

admin: root

password: 1234

1.更新源与安装curl：
```
apt update && apt install -y curl
```
2.安装依赖
```
bash <(curl -s https://raw.githubusercontent.com/V-Official-233/Argo-Xray-JS-render/main/main.sh)
```
3.下载文件
```
wget https://raw.githubusercontent.com/fscarmen2/Argo-Xray-JS-PaaS/main/entrypoint.sh https://raw.githubusercontent.com/fscarmen2/Argo-Xray-JS-PaaS/main/index.js https://raw.githubusercontent.com/fscarmen2/Argo-Xray-JS-PaaS/main/package.json
```
4.自行修改`entrypoint.sh`与`index.js`

具体请参考原项目README.md

5.安装依赖与Forever保护运行
```
npm i && npm i -g forever
```
6.运行项目
```
forever start index.js
```
（如果是使用token的话，可以加一个http:127.0.0.1:3000的隧道，这样就可以显示出项目本来的页面）
非token用户可以使用以下模板来连接
Vless
```
vless://{UUID}@skk.moe:443?security=tls&sni=[固定隧道的域名，记得把括号删掉]&type=ws&path=/gli-vless?ed%3D2048&host=[固定隧道的域名，记得把括号删掉]&encryption=none#Argo-Vless
```

欢迎PR