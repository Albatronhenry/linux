# linux

在使用SecureCRT登陆liunx（我的为CenterOS）系统，发现删除(backspace)键、和上下左右键不起作用，郁闷了很久没有找到解决办法，

今天终于看到了一篇有用的文章，在此记录一下！

解决方法：
  先打开Options–>Session Options–>Terminal–>Emulation(中文：选项–>回话选项–>终端–>仿真) 界面下 ：

1.终端(T):选择linux，默认为VT100.

2.ANSI颜色(A)打上勾。

然后打开Options–>Session Options–>Terminal–>Emulation–>Mapped Keys(中文：选项–>回话选项–>终端–>仿真–>映射键)

选中复选框  （Backspace sends delete、  Delete sends backspace）

[reference website](http://blog.csdn.net/zwx19921215/article/details/20803113)
