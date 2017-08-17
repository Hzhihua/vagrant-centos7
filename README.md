# centos7
>centos 7 Vagrant 开发环境（支持php版本切换，包含编译安装nginx，apache，mysql，php，redis，memcache，opache, 额外的ftp登录，phpmyadmin，composer） 2017/08/16

特别感谢 [OneinStack](https://oneinstack.com) [GitHub](https://github.com/lj2007331/oneinstack)

## 预览图
![change_php_version](https://raw.githubusercontent.com/wiki/Hzhihua/vagrant-centos7/change-php-version.png)

## 特色
- centos 7 64位
- [aliyun源](https://mirrors.aliyun.com/repo)
- 支持PHP版本切换（5.5 / 5.6 / 7.0）
- 全部软件通过编译安装
- 安装nginx（port: 80, version: 1.12.1, user: vagrant, group: vagrant）
- 安装apache（port: 88, version: 2.4.27, user:vagrant, group: vagrant）
- **为了统一nginx和apache的php接口，apache通过mod_proxy_fcgi连接PHP**
- PHP全部启用FastCGI进程管理器（FPM, user: vagrant, group: vagrant）
- MySQL（version: 5.6.37, username: root, password: 123123）
- 安装memcache（PHP7.0）
- 安装redis（PHP7.0）
- 安装Zend Opcache（PHP7.0, 默认关闭）
- phpMyAdmin
- FTP(未初始化)
- composer(version: 1.5.1, path: /usr/local/bin)
- 网站根目录：/data/wwwroot/default/
- 软件安装路径：/usr/local/
- mysql 数据文件：/data/mysql/data
- 日记文件:
    - apache：/data/wwwlogs/apache
    - nginx: /data/wwwlogs/nginx
    - php：/data/wwwlogs/php
    - mysql：/data/mysql

## 说明

> 由于网络墙问题，所以推荐下载box安装 
 
> 默认用户:vagrant 密码:vagrant

> root用户未激活，使用 sudo 提权

## 通过box安装
> ### install VirtualBox 5.1.24
> [https://www.virtualbox.org/wiki/Download_Old_Builds_5_1](https://www.virtualbox.org/wiki/Download_Old_Builds_5_1)

> ### install Vagrant 1.9.5
> [https://releases.hashicorp.com/vagrant/](https://releases.hashicorp.com/vagrant/)

> ### window平台，可选择git作为cmd命令行(自动补全)
> [https://git-scm.com/downloads](https://git-scm.com/downloads)

> ### 由于网络墙问题，所以上传至百度云  
> [https://pan.baidu.com/s/1mir8Y7Y](https://pan.baidu.com/s/1mir8Y7Y)  密码：99eb


> ### 如何用迅雷下载？？

打开控制台(F12)->点击console->输入
```angularjs
Object.defineProperty(this, 'navigator', {value: {platform: ""}});
```
按回车，点击下载即可弹出下载链接

```angularjs
mkdir centos7  #创建文件夹centos7
cd centos7  #进入文件夹centos7
vagrant box add centos7 /path/to/centos7.box  #以centos7.box文件为基础创建新的box
vagrant init centos7  #生成centos7 Vagranfile配置文件
vagrant up  #启动虚拟机
vagrant ssh  #登陆虚拟机
```

## 防火墙
> 默认关闭

详细参考：[http://www.cnblogs.com/kreo/p/4368811.html](http://www.cnblogs.com/kreo/p/4368811.html)

## 添加开机自启动
> 把php-fpm的脚本写好后放进/etc/rc.d/init.d/目录
```coffeescript
sudo chkconfig --add php-fpm
sudo chkconfig php-fpm on  # 启动
sudo chkconfig php-fpm off # 关闭
```

> 把启动程序的命令添加到/etc/rc.d/rc.local文件中

参考：[http://www.cnblogs.com/buffer/archive/2011/08/15/2138762.html](http://www.cnblogs.com/buffer/archive/2011/08/15/2138762.html)

## Apache
```coffeescript
sudo service httpd {start|graceful-stop|stop|graceful|restart|}
```
![apache](https://raw.githubusercontent.com/wiki/Hzhihua/vagrant-centos7/apache-curl.png)

## Nginx
```coffeescript
sudo service nginx {start|stop|status|restart|reload|configtest}
```
![nginx](https://raw.githubusercontent.com/wiki/Hzhihua/vagrant-centos7/nginx-curl.png)

## MySQL
```coffeescript
sudo service mysqld {start|stop|restart|reload|status}
```

## PHP
```coffeescript
sudo service php-fpm {start|stop|restart|reload|status}
```

## PHP版本切换
```cmd
cd ~/oneinstack
sudo ./change_php_version.sh
```
## 安装/卸载拓展
```coffeescript
cd ~/oneinstack
sudo ./vhost.sh
```

## 其他详细操作
参考：[https://oneinstack.com/install/](https://oneinstack.com/install/)

## 视频教程
[http://www.imooc.com/learn/805](http://www.imooc.com/learn/805)
