obj-m += mcp251x.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
test:
	sudo dmesg -C
	sudo insmod mcp251x.ko
	sudo ip link set can0 type can bitrate 1000000
	sudo ip link set can0 up
	dmesg

remove:
	sudo ip link set can0 down
	sudo rmmod mcp251x
show:
	ip -s -d link show can0

send:
	cansend can0 123#524551414C4C0A35
	dmesg
