CC=/usr/bin/g++
CFLAGS=-std=c++17 -g - o2 -Wall -pthread -I./
CXXFLAGS=-std=c++17 -g -Wall -pthread -I./
LDFLAGS= -lpthread -lrocksdb -lz -lsnappy -lnuma -lpmem
SUBDIRS= core db 
SUBSRCS=$(wildcard core/*.cc) $(wildcard db/*.cc)
OBJECTS=$(SUBSRCS:.cc=.o)
EXEC=ycsbc

all: $(SUBDIRS) $(EXEC)

$(SUBDIRS):
	$(MAKE) -C $@

$(EXEC): $(wildcard *.cc) $(OBJECTS)
	$(CC) $(CXXFLAGS) $^ $(LDFLAGS) -o $@

clean:
	for dir in $(SUBDIRS); do \
		$(MAKE) -C $$dir $@; \
	done
	$(RM) $(EXEC)

.PHONY: $(SUBDIRS) $(EXEC)

