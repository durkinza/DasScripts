BIN=key

SRCS=\
key.cpp\
smaz.cpp

OBJS=\
key.o\
smaz.o

HDRS=


CXX=g++

dbug=gdb



LIBS=

CXXFLAGS=-O3 -g -Wall -pedantic -Wno-write-strings 
#-Wc++11-compat-deprecated-writable-strings
#gcc -o smaz_test -O2 -Wall -W -ansi -pedantic smaz.c smaz_test.c
#CXXFLAGS=-g -Wall # use for debugging code

$(BIN): $(OBJS)
	#make smaz
	$(CXX) $(CXXFLAGS) $(OBJS) $(LIBS) -o $(BIN)

all : 
	touch $(SRCS)
	make

tar :
	tar -cvf $(BIN).tar $(SRCS) $(HDRS) makefile

debug : $(OBJS)
	$(CXX) -g $(OBJS) -o $(BIN) 
	$(dbug) $(BIN)

clean :
	rm -f $(OBJS) $(BIN) core
	
clobber :
	rm -f $(OBJS) $(BIN) core $(BIN) $(BIN).tar
