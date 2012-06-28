.. pylibmc

pylibmc
##################################################

Introduction
==================================================
pylibmc是python的memcached客户端，基于C版客户单libmemcached做的封装，是目前常见的memcached客户端中性能最好的。

Install
==================================================
Apt安装
--------------------------------------------------
Apt安装非常简单 ::

  sudo apt-get install libmemcached-dev
  pip install pylibmc

编译安装
--------------------------------------------------
编译安装这个东西费了牛劲，出了好多问题，这里是大概的过程::

  wget https://launchpad.net/libmemcached/1.0/1.0.6/+download/libmemcached-1.0.6.tar.gz
  tar libmemcached-1.0.6.tar.gz
  cd libmemcached-1.0.6
  ./configure --prefix=/opt/apps/libmemcached
  make -i && make -i install
  export CPPFLAGS="$CPPFLAGS -I/opt/apps/libmemcached"
  export LDFLAGS="$LDFLAGS -L/opt/apps/libmemcached"
  pip install pylibmc

出现的一些问题

- 编译到libmemcached/auto.cc的时候报错，PRIu64这个宏没有预处理。这个不知道为啥，
  在自己的电脑上编译没问题，换到服务器上就不行了。最后没办法把PRIu64替换为"lu"解决之。

- 编译一些测试代码的时候，会编一个自带的memcached, 依赖于libevent,但是把libevent的
  路径加到CPPFLAGS和LDFLAGS还是会报找不到符号，但是我自己下载memcached的源码编译一点
  问题没有，最后发现都是些测试代码，就直接忽略了。

- 编译这个东西卡了一天，学好C的冲动又加强了。
