# Snell
Snell server

1、一键搭建Snell安装教程

（1）安装 wget 依赖包

yum -y install wget #CentOS
apt-get install wget #Ubuntu/Debian

（2）执行Snell一键安装脚本（常规版）

1）执行一键安装脚本命令

Debian & Ubuntu 用户依次执行命令（AMD）：

wget --no-check-certificate -O snell.sh https://raw.githubusercontent.com/liczha/Snell/main/AMD/snell.sh
chmod +x snell.sh
./snell.sh

Debian & Ubuntu 用户依次执行命令（ARM）：

wget --no-check-certificate -O snell.sh https://raw.githubusercontent.com/liczha/Snell/main/ARM/snell.sh
chmod +x snell.sh
./snell.sh

2）修改Snell服务器运行端口

Snell首次安装完成的默认端口号为：13254，如需修改，请在以上所有脚本运行结束后运行如下命令：

nano /etc/snell/snell-server.conf #编辑 Snell 配置文件 systemctl restart snell #重启 Snell 服务器

snell-server.conf 各参数解析： listen = IP:端口 psk = 连接密码 obfs = 混淆方式

其中，obfs混淆一般支持“tls”或“http”两种方式，本脚本默认为“tls”混淆方式。

如果Snell服务器运行状态正常，那么执行查看Snell服务运行状态命令后显示“Active: active (running)”，即表示Snell服务成功运行。 3）Snell服务器管理命令

管理Snell服务命令：

systemctl status snell #查看运行状态
systemctl restart snell #重启Snell服务
systemctl start snell #启动Snell服务
systemctl stop snell #停止Snell服务
cat /etc/snell/snell-server.conf #查看Snell配置文件
vi /etc/snell/snell-server.conf #修改Snell配置文件

卸载Snell服务命令：

wget --no-check-certificate -O uninstall-snell.sh https://raw.githubusercontent.com/liczha/Snell/main/AMD/uninstall-snell.sh
chmod +x uninstall-snell.sh
./uninstall-snell.sh

2、一键安装并开启BBR加速

（1）安装 wget 依赖包、

yum -y install wget #CentOS
apt-get install wget #Ubuntu/Debian

（2）执行BBR加速一键安装脚本命令

cd /usr/src && wget -N --no-check-certificate "https://raw.githubusercontent.com/liczha/Snell/main/BBR/tcp.sh" && chmod +x tcp.sh && ./tcp.sh

选择“2”，“安装 BBRplus版内核”加速。在安装过程中，可能会出现如下提示，用右方向键选“”，然后回车。 安装完成后会提示重启服务器，这时候输入字母“y”，回车后，重启服务器。当服务器启动后，我们再次执行安装命令，选择“7”启用“使用BBRplus版加速”。

Snell客户端Surge配置 Proxy = snell, [SERVER ADDRESS], [GENERATED PORT], psk=[GENERATED PSK], obfs=tls
如：Proxy =snell，1.2.3.4:16888,psk=gl64TpuvRPRp0uLM,obfs=tls
