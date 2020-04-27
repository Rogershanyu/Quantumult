
进入Quantumult
1. 第一步:
    - 设置-订阅-右上'+'-服务器
    - 名称(自己命名)
    - 链接(复制下面,ps:我的服务器卡)需要请联系本人
    - 保存
    - 右拉刚刚添加的服务器点更新
2. 第二步:
    - 设置-分流-右上'+'
    - 类型:user-agent
    - 行为:选择第一步添加的服务器(建议选上海节点)
    - 匹配:NeteaseMusic*
    - 保存
    - 照上面方法把下面的都添加了
    ```
    类型,行为,匹配
    user-agent,节点名称,NeteaseMusic*
    user-agent,节点名称,NeteaseMusic**
    user-agent,节点名称,网易云音乐*
    user-agent,节点名称,网易云音乐**
    user-agent,节点名称,%E7%BD%91%E6%98%93%E4%BA%91%E9%9F%B3%E4%B9%90*
    user-agent,节点名称,%E7%BD%91%E6%98%93%E4%BA%91%E9%9F%B3%E4%B9%90**
    ```
    
3. 第三步:
    - 设置-运行模式-自动分流
    
4. 第四步:
    - 点击下面中间的图标(设置右边统计左边的图标)
    - 选择GCS HK01(如果已经选择了GCS HK01点白色处推出就可以)
5. 第五步:
    - 首页-右上角打开(其实这时可以科学上网了)



- 用safari浏览器打开`https://raw.githubusercontent.com/nondanee/UnblockNeteaseMusic/master/ca.crt`
- 会弹出 [ 此网站尝试下载一个配置描述文件.你要允许吗? ] 点击允许,然后弹出 [ 已经下载描述文件 ] 点击关闭
- 退出safari浏览器,进入手机设置,点击已下载描述文件(如果设置首页没找到就进入 通用-描述文件-UnblockNeteaseMusic Root CA)
- 点击安装(不要问我密码是什么,你自己手机的密码,我也不知道)
- 安装好就进入 设置(手机设置)-通用-关于本机-证书信任设置(最下面) 把UnblockNeteaseMusic Root CA打开,点击继续(这里已经解锁网易云音乐了)








---------------------这里给有需要的人看的------------------------
搭服务器教程(自己备一台vps):
1. 安装Nodejs
- #Debian/Ubuntu系统 
 ```
curl -sL https://deb.nodesource.com/setup_10.x | bash -
apt install -y nodejs git
```
- #CentOS系统 
```
curl -sL https://rpm.nodesource.com/setup_10.x | bash -
yum install nodejs git -y
```
2. 下载github里面的UnblockNeteaseMusic项目
```
git clone https://github.com/nondanee/UnblockNeteaseMusic.git
cd UnblockNeteaseMusic
```

3. 开机自启
    这里使用Systemd进程守护，只适用于CentOS 7、Debian 8+、Ubuntu 16+等。
    #修改下ExecStartPre源码路径即可，然后一起复制到SSH运行 
```
cat > /etc/systemd/system/UnblockNeteaseMusic.service <<EOF
[Unit]
Description=UnblockNeteaseMusic
After=network.target
Wants=network.target

[Service]
Type=simple
PIDFile=/var/run/UnblockNeteaseMusic.pid
WorkingDirectory=/root/UnblockNeteaseMusic
ExecStart=/usr/bin/node app.js -s -e https://music.163.com -p 19980:8081
RestartPreventExitStatus=23
Restart=always

[Install]
WantedBy=multi-user.target
EOF
```
4. 启动并开机自启：
```
systemctl start UnblockNeteaseMusic 
systemctl enable UnblockNeteaseMusic 
systemctl status UnblockNeteaseMusic 
```
