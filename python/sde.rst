.. python development environment

Dev Environment
##################################################

*工欲善其事，必先利其器。软件开发时一套完善的开发环境是必不可少的，整理下自己的开发环境*

操作系统
==================================================

    Ubuntu。一般linux系统都会装有python的运行环境，但是版本会比较低，如果想要高版本的python的话，只能自己编译，或者找别人编译好的二进制包来装。我目前用的是Ubuntu11.10，自带的python版本是2.7.2的，该版本是2.X版本的最高版本，2.X相对还是要普及些.

安装Python
==================================================

    编译安装2.7.3，貌似在centos,redhat下面有个bug，在装sqlite的包时会失败，用下面的安装步骤 ::
        
        curl -sk https://raw.github.com/gist/2727063/ | patch -p1
        ./configure --prefix=/opt/apps/python2 --enable-shared --enable-profiling
        make
        make install


    觉得系统自带的python版本比较低的话，可以apt自动安装。(3.2版本是目前正式发布的最高版本) ::

	sudo apt-get install python3.2
    

    如果想折腾下自己编译的话，可以下载源码包，解压并进入目录，执行如下命令 ::

        sudo apt-get build-dep python3
        ./configure --prefix=/opt/apps/python3 --enable-shared --enable-profiling
        make
        make install 

	
easy_install
==================================================
python的自动化安装工具。公司用的话，可以搭个pypi的私服，让easy_install去连。
 
pip
==================================================
easy_install的进化版, pip的安装 ::
  
      sudo easy_install pip
virtualenv
==================================================
virtualenv能够创立一个独立的python运行环境，可以用它实现测试和正式开发环境的分离。

- virtualenv安装 ::

      sudo pip install virtualenv

- virtualenv使用 ::

      virtualenv /opt/pyenvs/devp
      source /opt/pyenvs/devp/bin/activate
      virtualenv_deactivate
执行完命令后，会在shell前面出现一个devp的提示，表示已经激活了该环境。

virtualenvwrapper
--------------------------------------------------
如果你的环境很多的话，来回切换敲要敲好多行命令会很不方便，可以试下virtualenvwrapper。

- virtualenvwrappe的安装 ::

      sudo pip install virtualenvwrapper

- virtualenvwrappe的使用 ::
      
      export WORKON_HOME=/opt/pyenvs
      source /usr/local/bin/virtualenvwrapper.sh
      mkvirtualenv devp
      mkvirtualenv prod
      workon devp
      rmvirtualenv
      lssitepackages
      
IDE
==================================================
个人感觉eclipse + pydev 已经比较好了。最近在学emacs，以后逐步用emacs来开发吧。


Reference
==================================================
`pip的使用文档 <http://www.pip-installer.org/en/latest/index.html>`_
