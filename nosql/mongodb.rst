.. MongoDB

MongoDB
##################################################

MongoDB安装
==================================================

RedHat5，64位
--------------------------------------------------
创建/etc/yum.repos.d/10gen.repo文件，内容如下 ::

  [10gen]
  name=10gen Repository
  baseurl=http://downloads-distro.mongodb.org/repo/redhat/os/x86_64
  gpgcheck=0
  enabled=1

执行下面的下面的命令安装 ::

  yum update
  yum install mongo-10gen mongo-10gen-server

这样mongodb已经安装好了，执行service mongod start就可以启动mongodb server了。

下面安装mongodb的GUI管理工具 `RockMongo <http://rockmongo.com/>`_,这个东西是用php写的web管理端，所以要安装php，php的版本最好是5.3以上的版本（安装php的时候出了问题，rockmongo的官方文档貌似是支持最低版本5.1.6的，redhat官方源自带的php，版本就是5.1.6的，但是在安装mongodb的php驱动的时候编译失败，把php升级到5.4版本，就OK了），下面简单列下安装步骤，执行下面的命令 ::
  rpm -ivh http://mirrors.ustc.edu.cn/fedora/epel/5/x86_64/epel-release-5-4.noarch.rpm
  rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-5.rpm
  yum update
  yum install httpd.x86_64
  yum install php.x86_64
  git clone git://github.com/mongodb/mongo-php-driver.git
  cd mongo-php-driver
  phpize
  ./configure
  make && make install
  cd /var/www/html
  wget http://rock-php.googlecode.com/files/rockmongo-v1.0.11.zip
  unzip rockmongo-v1.0.11.zip
  #编辑/etc/php.ini文件，添加extension=mongo.so
  httpd -k stop
  httpd -k start
