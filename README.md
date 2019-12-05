1.下载一键搭建ss脚本文件（直接在绿色光标处复制该行命令回车即可，只需要执行一次，卸载ss后也不需要重新下载）

git clone -b master https://github.com/meizizi9996/meizizi

如果提示bash: git: command not found，则先安装git（你如果不知道自己是哪个系统，那就全部执行一次，然后再执行上面的那个下载命令）：

Centos系统执行这个： yum -y install git
Ubuntu/Debian系统执行这个： apt-get -y install git

2.运行搭建ss脚本代码

meizizi/ss-fly.sh -i password 端口
注意：如果提示Permission denied
解决的办法：
$ sudo chmod -R 777 某一目录
注：如果需要改密码或者改端口，只需要重新再执行一次搭建ss脚本代码就可以了，或者修改/etc/shadowsocks.json这个配置文件（如何修改在公众号回复vim编辑器使用）。

3.相关ss操作 

修改配置文件：vim /etc/shadowsocks.json
停止ss服务：ssserver -c /etc/shadowsocks.json -d stop
启动ss服务：ssserver -c /etc/shadowsocks.json -d start
重启ss服务：ssserver -c /etc/shadowsocks.json -d restart
4.卸载ss服务

ss-fly/ss-fly.sh -uninstall


一键开启BBR加速
BBR是Google开源的一套内核加速算法，可以让你搭建的shadowsocks/shadowsocksR速度上一个台阶，本一键搭建ss/ssr脚本支持一键升级最新版本的内核并开启BBR加速。

BBR支持4.9以上的，如果低于这个版本则会自动下载最新内容版本的内核后开启BBR加速并重启，如果高于4.9以上则自动开启BBR加速，执行如下脚本命令即可自动开启BBR加速：

meizizi/ss-fly.sh -bbr


装完后需要重启系统，输入y即可立即重启，或者之后输入reboot命令重启。

判断BBR加速有没有开启成功。输入以下命令：

sysctl net.ipv4.tcp_available_congestion_control
如果返回值为：

net.ipv4.tcp_available_congestion_control = bbr cubic reno
只要后面有bbr，则说明已经开启成功了。
