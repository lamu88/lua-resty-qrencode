CC      := gcc
LD      := ld
CFLAGS  := -I${OPENSHIFT_DATA_DIR}usr/local/libqrencode/include -fPIC
LIB	:= -lpng
LDFLAGS := -L${OPENSHIFT_DATA_DIR}usr/local/libqrencode/lib -shared -fpic
SOURCE  := $(wildcard *.c)
OBJS    := $(patsubst %.c,%.o,$(SOURCE))
TARGET_LIB := libimg.so

all:$(OBJS)
	@echo $(OBJS)
	$(LD) $(LDFLAGS) $(LIB) -o $(TARGET_LIB) $(OBJS) 
	@rm *.o -rf

%.o:%.c
	@echo Compiling $< ...
	@$(CC) -c $(CFLAGS)  $< -o $*.o

.PHONY: clean

clean:
	rm *.so *.o -rf
	
install:
	cp libimg.so ${OPENSHIFT_DATA_DIR}usr/local/luajit/lib/
	cp ../lib/resty/*.lua ${OPENSHIFT_DATA_DIR}lualib/resty/
