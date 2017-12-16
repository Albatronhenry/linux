### linux
* 安装好了nginx，却无法站外访问（老是显示连接超时）

```
[root@localhost conf]# Connecting to 192.168.201.128:80  failed to host
```
原因是CentOS的防火墙把80端口拦截住了，尝试以下命令得以解决
```
[root@localhost ~]# iptables -I INPUT -p tcp --dport 80 -j ACCEPT
[root@localhost ~]# /etc/init.d/iptables status
表格：filter
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
2    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:8080 
3    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:3306 
4    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
5    ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
6    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
7    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:22 
8    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:6379 
9    REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-prohibited 

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         
1    REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-prohibited 

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination 
```

我们可以看到80端口打开了：`ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 `

然后我们尝试浏览器输入`http://ip:port`就可以访问了。

[referencewebsite](http://www.360doc.com/content/16/0105/17/12146850_525690022.shtml)
