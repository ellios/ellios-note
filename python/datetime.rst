.. time transform

时间转化
##################################################

string > number
==================================================
::

  >>> t=time.strptime('2007/4/15','%Y/%m/%d')
  >>> t.mktime()
  1176566400.0
  

number > string
==================================================
::

  >>> t = time.localtime(1176566400.0)
  >>> time.strftime("%Y-%m-%d %H-%M-%S", t)
  '2007-04-15 00-00-00'
  
string > java System.currentTimeMillis
==================================================
java的currentTimeMillis计算出来的时间戳是精确到毫秒的, 需要降级精确到秒 ::

  >>> t=time.strptime('2007/4/15','%Y/%m/%d')
  >>> t.mktime() * 1000
  1176566400000.0

java System.currentTimeMillis > string
==================================================
::

  >>> t = time.localtime(1176566400000/1000)
  >>> time.strftime("%Y-%m-%d %H-%M-%S", t)
  '2007-04-15 00-00-00'

