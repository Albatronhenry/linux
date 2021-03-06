### linux--Java连接虚拟机的redis报错问题解决办法

Eclipse执行下列代码：
```java
public class TestPing {

public static void main(String[] args) {
Jedis jedis = new Jedis("192.168.201.128", 6379);
System.out.println(jedis.ping());
	}
}
```

1:redis.clients.jedis.exceptions.JedisConnectionException: java.net.SocketTimeoutException: connect timed out

借鉴一些网友的解决方案：

关闭虚拟机的防火墙

```
     1）暂时关闭防火墙：/etc/init.d/iptables stop

     2) 重启虚拟机生效：chkconfig iptables off   或者 /sbin/chkconfig --level 2345 iptables off
```

2.继续运行上述代码，报错如下：
```java
Exception in thread "main" redis.clients.jedis.exceptions.JedisConnectionException: java.net.ConnectException: Connection refused: connect
```
解决方案，修改redis.conf配置文件，将端口号127.0.0.1注释掉，这样任何IP都能访问，

```linux
[root@localhost bin]# cd /usr/local/redis/bin
[root@localhost bin]# ls
dump.rdb         redis-check-aof   redis-cli   redis-sentinel
redis-benchmark  redis-check-dump  redis.conf  redis-server
[root@localhost bin]# vi redis.conf
```
注释（关键词前面加上 #  即可）其中的bind（

#### vi中查找关键字方法：

---------------------------------------------------------
关于如何当你用vi打开一个文件后，因为文件太长，如何
才能找到你所要查找的关键字呢？ 
在vi里可没有菜单-〉查找 
不过没关系，你在命令模式下敲斜杆( / )这时在状态栏
（也就是屏幕左下脚）就出现了 “/” 然后输入你要查找的关键字（bind)敲回车就可以了。 
如果你要继续查找此关键字，敲字符 n 就可以继续查找了。

--------------------------------------------------------------
保存退出后，运行代码，发现报错依旧，因为尚未启动redis服务，启动redis服务

```linux
[root@localhost redis]# ls
bin  redis-3.0.7  redis-3.0.7.tar.gz
[root@localhost redis]# cd bin
[root@localhost bin]# ls
dump.rdb         redis-check-aof   redis-cli   redis-sentinel
redis-benchmark  redis-check-dump  redis.conf  redis-server
[root@localhost bin]# ./redis-server redis.conf（在对应目录下找到--   启动指令为    ./    或者使用    sh
```
遇到请求被拒，设置永久启动方法
修改redis.conf配置文件， daemonize yes 以后端模式启动。

执行如下命令启动redis：
```linux
cd /usr/local/redis
./bin/redis-server ./redis.conf
```
redis默认使用6379端口。

也可更改redis.conf文件，修改端口号：


最后运行代码，控制台输出PONG，即解决


[ reference website ](http://blog.csdn.net/oxinliang12/article/details/52279143)

