PROGRAMS = vars1 vars2 vars3 vars4 ptr struct union addrspace

all: $(PROGRAMS)

ALLPROGRAMS = $(PROGRAMS)

include ../common/rules.mk

# As we're demoing undefined behavior in some ways, let us not complain
# about uninitialized variables
CFLAGS:=$(filter-out Wuninitialized,$(CFLAGS))

%.o: %.c $(BUILDSTAMP)
	$(CC) $(CPPFLAGS) $(CFLAGS) $(DEPCFLAGS) $(O) -o $@ -c $<

vars: vars.o hexdump.o
	$(CC) $(CFLAGS) $(O) -o $@ $^

clean:
	rm -f $(ALLPROGRAMS) *.o
	rm -rf $(DEPSDIR) *.dSYM

.PHONY: all clean
