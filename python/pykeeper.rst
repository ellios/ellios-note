.. pykeeper

pykeeper
##################################################


Install
==================================================

.. code-block:: python

  wget http://labs.renren.com/apache-mirror/zookeeper/zookeeper-3.4.3/zookeeper-3.4.3.tar.gz
  tar -xzf zookeeper-3.4.3.tar.gz
  cd zookeeper-3.4.3/src/c
  ./configure --prefix=/opt/apps/zookeeper
  make && make install
  export CPPFLAGS="$CPPFLAGS -I/opt/apps/zookeeper/include/zookeeper"
  export LDFLAGS="$LDFLAGS -L/opt/apps/zookeeper/lib"
  pip install zkpython
  pip install pykeeper
  
