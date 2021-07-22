CXX = g++
CFLAGS = -std=c++14 -O2 -Wall -g 

TARGET = WebServer
OBJS = ../code/log/*.cpp ../code/timer/*.cpp \
       ../code/sqlconnpool/*.cpp \
       ../code/http/*.cpp ../code/server/*.cpp \
       ../code/buffer/*.cpp ../code/main.cpp

all: $(OBJS)
	$(CXX) $(CFLAGS) $(OBJS) -o ../serverbin/$(TARGET)  -pthread -lmysqlclient

clean:
	rm -rf ../bin/$(OBJS) $(TARGET)
