.. cx_Oracle

cx_Oracle
##################################################


Usage
==================================================
- connect ::
  
  conn = cx_Oracle.connect('user/pass@host:port/')
  cur = conn.cursor()

- close ::

  cur.close()
  conn.close()

- select where ::

  cur0.execute("select id, xxx from table where id = :1", xxx) 
  
- select where in ::

  cur0.execute("select id, xxx from table where id in {}".format((xxx, xxx)))


FAQ
==================================================

编码
--------------------------------------------------
1. 查看数据库当前字符集设置
  
.. code-block:: SQL

  select * from nls_database_parameters
  select userenv(‘language’) from dual

2. 设置客户端字符集,oracle会通过NLS_LANG这个环境变量获取字符集信息，这个值要和服务器的字符集一致。::

  os.environ["NLS_LANG"]=".zhs16gbk"

.. attention::

  todo，貌似还有些问题，慢慢再完善吧。
  
  

