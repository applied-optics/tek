include ../../config.mk

.PHONY:	all clean install

CFLAGS:=$(CFLAGS) -I../../library

all:	tek_afg

tek_afg: tek_afg.o
	$(CXX) -o $@ $^ -lvxi11 $(LDFLAGS)

tek_afg.o: tek_afg.cc
	$(CXX) $(CFLAGS) -c $^ -o $@

clean:
	rm -f *.o tek_afg

install : all
	$(INSTALL) tek_afg $(DESTDIR)$(prefix)/bin/

