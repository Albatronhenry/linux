### [CentOS下ZooKeeper环境搭建](http://www.linuxidc.com/Linux/2016-12/137958.htm)

Zookeeper的安装：

第一步：安装jdk

第二步：解压缩zookeeper压缩包

第三步：将conf文件夹下zoo_sample.cfg复制一份，改名为zoo.cfg

第四步：修改配置dataDir属性(vi zoo.cfg)，指定一个真实目录

第五步：

启动zookeeper：bin/zkServer.sh start

关闭zookeeper：bin/zkServer.sh stop

查看zookeeper状态：bin/zkServer.sh status


注意要关闭linux的防火墙:

解决方法：

检查防火墙是否关闭，service iptables stop;

检查三台机器是否均已启动，可通过jps查看，有QuorumPeerMain进程代表当前机器zookeeper已经启动（但启动成功与否无法判断）

![jps](https://github.com/Albatronhenry/UploadFile/blob/master/pic/jps.png)
