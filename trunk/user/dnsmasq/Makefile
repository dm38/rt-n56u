SRC_NAME=dnsmasq-git

COPTS := -DHAVE_BROKEN_RTC -DNO_INOTIFY -DNO_AUTH -DNO_LOOP
ifndef CONFIG_IPV6
COPTS += -DNO_IPV6
endif
ifndef CONFIG_USB_SUPPORT
COPTS += -DNO_TFTP
endif
ifneq ($(CONFIG_FIRMWARE_INCLUDE_IPSET),y)
COPTS += -DNO_IPSET
endif

all:
	$(MAKE) -C $(SRC_NAME) COPTS="$(COPTS)"

clean:
	$(MAKE) -C $(SRC_NAME) clean
	rm -f dnsmasq

romfs:
	cp $(SRC_NAME)/src/dnsmasq .
	$(STRIP) dnsmasq
	$(ROMFSINST) /usr/sbin/dnsmasq
