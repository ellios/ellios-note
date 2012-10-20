.. proto buffer

proto buffer
##################################################


install
==================================================

::

   ./configure --prefix=/opt/install/protobuf
   make
   make install

- 编译java的库 ::

    cd java
    mvn clean install -Dmaven.test.skip=true

- 安装python的库 ::

    pip install protobuf


CPP的编译Makefile
--------------------------------------------------

Makefile ::

   CXXFLAGS =	-O2 -g -Wall -fmessage-length=0
   CPPFLAGS = -I/opt/install/protobuf/include
   LDFLAGS = -L. -L/opt/install/protobuf/lib 

   OBJS =		address_book_example.o tutorial.pb.o

   LIBS =

   TARGET =	address_book_example

   $(TARGET):	$(OBJS)
	$(CXX) ${LDFLAGS} -o $(TARGET) $(OBJS) $(LIBS) -lprotobuf -lpthread

   all:	$(TARGET)

   clean:
	rm -f $(OBJS) $(TARGET)
