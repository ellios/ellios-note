.. zeroc-ice install

Install
##################################################

Python客户端安装
==================================================

apt安装
--------------------------------------------------
Ubuntu的apt有ICE的源，直接用apt安装就好了 ::

  sudo apt-get install python-zeroc-ice

yum安装
--------------------------------------------------

- 添加源， ::

    cd /etc/yum.repos.d/
    wget http://www.zeroc.com/download/Ice/3.4/rhel5/zeroc-ice.repo
  
- 编辑zeroc-ice.repo, 如下 ::

    [zeroc-ice]
    name=Ice 3.4b for RHEL $releasever - $basearch
    baseurl=http://www.zeroc.com/download/Ice/3.4/rhel5/$basearch
    enabled=0
    gpgcheck=1
    gpgkey=http://www.zeroc.com/download/RPM-GPG-KEY-zeroc-beta  
		  
- 安装 ::

    yum install ice-python.x86_64

编译安装
--------------------------------------------------

官方的二进制包只有python2.4的包，只能自己安装了，貌似编译这个Ice要编译一大堆东西.我的python是自己编译的，如果系统自带的话要装python-devel的包。 

- 编译依赖的包 ::
  
    wget http://www.zeroc.com/download/Ice/3.4/ThirdParty-Sources-3.4.2.tar.gz
    tar xzf ThirdParty-Sources-3.4.2.tar.gz
    cd ThirdParty-Sources-3.4.2
    tar xzf  mcpp-2.7.2.tar.gz && cd mcpp-2.7.2
    patch -p0 < ../mcpp/patch.mcpp.2.7.2 
    ./configure CFLAGS=-fPIC --enable-mcpplib --disable-shared 
    make && make install

还有一些其他的包，不过目前的系统提前都装过了，只需要一个mcpp， 其他的包以后慢慢补充吧.

- 编译ice ::
  
    wget http://www.zeroc.com/download/Ice/3.4/Ice-3.4.2.tar.gz
    tar xzf Ice-3.4.2.tar.gz
    cd  Ice-3.4.2/cpp
    export ICE_HOME=/opt/apps/Ice
    修改config/Make.rules将prefix的路径改为/opt/apps/Ice
    make && make install
    export PATH+=$ICE_HOME/bin
    export LD_LIBRARY_PATH+=/opt/apps/Ice/lib64
    cd ../py
    修改config/Make.rules将prefix的路径改为/opt/apps/Ice 
    make && make install
    export PYTHONPATH=$PYTHONPATH:/opt/apps/Ice/python/

- 费牛劲，编了有半个多小时，终于编译完了，体验下，进入python ::
  
    >>> import Ice

没有错误提示就表示好了

Reference
==================================================
`ICE在Linux下的完整编译安装 <http://blog.chaoskey.com/2008/08/23/126>`_
