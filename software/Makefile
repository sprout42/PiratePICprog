EXE=picprog
EXECS= $(EXE) compare
CC = gcc
VERSION = $(shell git branch --show-current)-$(shell git describe --always)
CFLAGS = -g -O0 -std=gnu99 -DVERSION=\"$(VERSION)\"

LDFLAGS =

OBJS_COMMON = memory.o data_file.o common.o debug.o

OBJS = $(OBJS_COMMON)
OBJS += pic.o proto_pic.o pic12.o pic16.o pic18.o pic24.o pic32.o
OBJS += iface.o buspirate.o serial.o

all: $(EXECS)


$(EXE):  $(OBJS) main.o
	$(CC) $(CFLAGS) -o $(EXE) $(OBJS) main.o $(LFD_OBJS) $(LDFLAGS)

compare:  $(OBJS_COMMON) compare.o
	$(CC) $(CFLAGS) -o compare $(OBJS_COMMON) compare.o $(LFD_OBJS) $(LDFLAGS)

%.o:	%.c
	$(CC) $(CFLAGS) $(DEFS) -c $<

clean:
	rm -f $(EXECS) *.o

