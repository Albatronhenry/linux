### [securecrt 遇到一个致命的错误且必须关闭](http://blog.csdn.net/lisheng19870305/article/details/45537759)

问题描述：

1、以前安装使用正常SecureCRT，现在出现问题：

2、出现的错误：

    遇到一个致命的错误且必须关闭
    
3、解决方案：

1）找到SecureCRT.dmp文件并删除

2）删除注册表信息


	 cmd打开RegEdit 
   
   打开HKEY_LOCAL_MACHINA,CTRL+F找到其SOFTWARE里也有VanDyke，将其删除。(如果存在删除)
   
   打开HKEY_CURRENT_USER,其SOFTWARE里也有VanDyke，将其删除。(如果存在删除)


3）打开SecureCRT，正常



