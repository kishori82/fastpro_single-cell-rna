CC := g++
CFLAGS := -Wall -g -I../libStatGen/include -I../htslib-1.13/htslib  -I../htslib-1.13 -I../gzstream
TARGET := test

# $(wildcard *.cpp /xxx/xxx/*.cpp): get all .cpp files from the current directory and dir "/xxx/xxx/"
SRCS := $(wildcard *.cpp)

# $(patsubst %.cpp,%.o,$(SRCS)): substitute all ".cpp" file name strings to ".o" file name strings
OBJS := $(patsubst %.cpp,%.o,$(SRCS))

all:	$(OBJS)

%.o: %.cpp
	$(CC) $(CFLAGS) -c $<
clean:
	rm -rf *.o
	
.PHONY: all clean
