### linux

* linux服务器上安装MySQL5.5时报了如下错

`/usr/bin/perl is needed by MySQL-server-...`

按照网上的几种说法进行了尝试

1、在perl官网下载perl后安装到相应的目录下，仍无法解决问题

2、采用强制安装 rpm -ivh MySQL-server-5.6.22-1.el6.i686.rpm --nodeps  依然无效



参考 http://www.iteye.com/problems/130971 中的方法

安装下面这个依赖

`yum install -y perl-Module-Install.noarch`



MySQL成功安装!!!



