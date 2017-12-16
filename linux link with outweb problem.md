### linux


linux (ifconfig -a) eth0 no ip & ip is  127.0.0.1


* solve method:

输入`ifconfig`后，显示为`127.0.0.1`

在linux系统中输入命令:
```
vi  /etc/sysconfig/network-scripts/ifcfg-eth0 
```
然后显示如下结果
点击I或者是A进入可编辑状态(需要先切换到管理员帐号下，自行百度)

将其中的`ONBOOT=no`改为`yes`,

点击`Esc`，

然后输入 `:wq`,

敲击`enter`保存并退出.

最后输入命令: 

```
service network restart（重启服务命令）
```
重启服务器,会出现正在配置IP的提示,待自动配置成功后,输入命令ifconfig即可.

[reference website ](http://blog.csdn.net/qq_36769100/article/details/71473632?fps=1&locationNum=5)




