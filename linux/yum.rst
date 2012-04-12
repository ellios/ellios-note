.. yum

yum
##################################################

Configuration
==================================================




Repository
==================================================

epel&remi
--------------------------------------------------
remi和epel上有些常用的开发库。添加方式如下 ::
  
  wget http://dl.fedoraproject.org/pub/epel/5Server/x86_64/epel-release-5-4.noarch.rpm
  wget http://rpms.famillecollet.com/enterprise/5/remi/x86_64/remi-release-5-8.el5.remi.noarch.rpm
  rpm -ivh epel-release-5-4.noarch.rpm remi-release-5-8.el5.remi.noarch.rpm
							 
