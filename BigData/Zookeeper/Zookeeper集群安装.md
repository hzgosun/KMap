# 1、前提准备3台虚拟机
```
 m1:192.168.243.132
 m2:192.168.243.133
 m3:192.168.243.134
```
# 2、并在三台虚拟机上配置hosts为
```
192.168.243.132 m1
192.168.243.133 m2
192.168.243.134 m3
```
# 3、下载zookeeper并解压
```
wget http://apache.fayea.com/zookeeper/zookeeper-3.4.10/zookeeper-3.4.10.tar.gz
tar -zxvf zookeeper-3.4.10.tar.gz
chmod +wxr zookeeper-3.4.10
```
# 4、修改zookeeper的配置文件，并建立数据目录和日志目录
```
cd zookeeper-3.4.10
mkdir data
mkdir logs
mv conf/zoo_sample.cfg zoo.cfg  （zoo_sample.cfg为样例配置文件，需要修改为自己的名称，一般为zoo.cfg）
vi conf/zoo.cfg
``` 
![zoo.cfg](https://github.com/lsy521/KMap/blob/master/Picture/Zookeeper/149861.gif)
### initLimit
```
ZooKeeper集群模式下包含多个zk进程，其中一个进程为leader，余下的进程为  follower。当follower最初与leader建立连接时，它们之间会
传输相当多的数据，尤其是follower的数据落后leader很多。initLimit配置follower与leader之间建立连接后进行同步的最长时间。
```
### syncLimit
```
配置follower和leader之间发送消息，请求和应答的最大时间长度。
```
### tickTime
```
tickTime则是上述两个超时配置的基本单位，例如对于initLimit，其配置值为5，说明其超时时间为 2000ms * 5 = 10秒。
```
### server.id=host:port1:port2 
```
其中id为一个数字，表示zk进程的id，这个id也是dataDir目录下myid文件的内容。 
host是该zk进程所在的IP地址，port1表示follower和leader交换消息所使用的端口，port2表示选举leader所使用的端口。
```
### dataDir 
```
其配置的含义跟单机模式下的含义类似，不同的是集群模式下还有一个myid文件。myid文件的内容只有一行，且内容只能为1 - 255之间的数字，
这个数字亦即上面介绍server.id中的id，表示zk进程的id。
```
# 5、进入dataDir目录修改myid文件
```
vi myid
三台机器dataDir目录（zoo.cfg配置中dataDir目录）下，分别生成一个myid文件，其内容分别为1，2，3（与zoo.cfg配置中的server.1对应），
myid文件的内容只有一行，且内容只能为1 - 255之间的数字，这个数字亦即上面介绍server.id中的id，表示zk进程的id
```
# 6、设置环境变量
```
创建一个环境变量ZOOKEEPER并把该环境变量添加到系统路径：
vim /etc/profile
添加ZOOKEEPER_HOME,修改PATH文件
export ZOOKEEPER_HOME=/usr/zookeeper/zookeeper-3.4.10
export PATH=$PATH:$JAVA_HOME/bin:$HADOOP_HOME/bin:
$HADOOP_HOME/sbin:$ZOOKEEPER_HOME/bin
source /etc/profile 保存配置
```
# 7、安装成功，进行测试
```
  进入bin目录
　　1、启动
      sh zkServer.sh start
　　2、查看状态
      sh zkServer.sh status
　　3、停止
      sh zkServer.sh stop
