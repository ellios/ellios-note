.. Redis

Redis
##################################################

Redis安装
==================================================
::

   make
   make PREFIX=/home/tools/redis install


Redis配置
==================================================

* 目前在用的配置，主要用作内存数据库，需要主从，数据大概1G。 `传送门 <https://gist.github.com/3884672>`_
* `配置中文说明 <http://blog.chinaunix.net/uid-429659-id-3158013.html>`_

Redis运行
==================================================
::

   echo vm.overcommit_memory=1 >> /etc/sysctl.conf
   sysctl vm.overcommit_memory=1 
   redis-server redis.conf


Redis使用
==================================================
* `Redis数据备份与恢复 <http://haili.me/archives/335>`_
* `Redis数据持久化 <http://blog.nosqlfan.com/html/3813.html>`_
* `http://www.infoq.com/cn/articles/tq-redis-memory-usage-optimization-storage`

Redis监控
==================================================

* `http://ylw6006.blog.51cto.com/470441/1006313`
