CC=ldc2
#CFLAGS=-betterC -c -release -boundscheck=on -O1 -enable-inlining -disable-red-zone
CFLAGS=-betterC -c -release -boundscheck=on -enable-inlining -aarch64-enable-cond-br-tune -aarch64-enable-condopt
#CFLAGS=-betterC -c
ext=.o_shipped
CC_PATH=~/dlang/ldc-1.14.0/activate
SHELL := /bin/bash
SRC=$(wildcard *.d)
TAR=$(SRC:.d=.o_shipped)
D_FLAGS=-d-version=CONFIG_LOCKDEP,CONFIG_DEBUG_LOCK_ALLOC,CONFIG_DEBUG_SPINLOCK,CONFIG_NETPOLL,CONFIG_64BIT,CONFIG_MUTEX_SPIN_ON_OWNER,CONFIG_DEBUG_MUTEXES,CONFIG_SMP,CONFIG_NET_NS,CONFIG_IPV6,CONFIG_SYSFS,CONFIG_NETFILTER_INGRESS,CONFIG_RFS_ACCEL,CONFIG_XPS,CONFIG_XFRM,CONFIG_IPV6_NDISC_NODETYPE,CONFIG_NET_RX_BUSY_POLL,CONFIG_ARCH_DMA_ADDR_T_64BIT,CONFIG_NEED_SG_DMA_LENGTH,CONFIG_SPARSEMEM,CONFIG_SPARSEMEM_VMEMMAP,CONFIG_NR_CPUS

all: build

build: $(TAR) copy

%.o_shipped: %.d
	source $(CC_PATH) && $(CC) $(CFLAGS) $(D_FLAGS) $< -of=$@

copy:
	mv $(TAR) ..

print:
	echo $(TAR)

clean:
	cd .. ; rm -f $(TAR); rm -f virtio_net_tmp* virtio_net.o

