#CC=rsdk-linux-gcc

include  $(DIR_LINUX)/.config

CFLAGS := -s -Wall -c -Os $(CFLAGS)
LDFLAGS = -s -Wall

ifeq ($(SLINK),1)
CFLAGS  += -ffunction-sections -fdata-sections
LDFLAGS += --static -s -Wl,--gc-sections
endif

ifeq ($(CONFIG_RTL_11V_SUPPORT),y)
CFLAGS += -DCONFIG_IEEE80211V
endif

all:		dot11k_deamon

dot11k_deamon:		dot11k_deamon.o
			$(CC) $(LDFLAGS) -o dot11k_deamon dot11k_deamon.o 

clean:
			rm -f *.o
			rm -f dot11k_deamon

romfs:
	$(ROMFSINST) dot11k_deamon /bin/dot11k_deamon

dot11k_deamon.o:		dot11k_deamon.c 
			$(CC) $(CFLAGS) -o dot11k_deamon.o dot11k_deamon.c
