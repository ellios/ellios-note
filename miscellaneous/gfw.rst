.. gfw

翻越XXX墙
##################################################

原理：

建立动态隧道


前提：

    要有一台在墙外的机器，而且能通过ssh连上该机器

windows翻墙：看下面的图:

.. image:: ../images/putty-tunnel.png

linux翻墙，执行下面的命令::
  
  ssh -N -f -D port user@ip
    

