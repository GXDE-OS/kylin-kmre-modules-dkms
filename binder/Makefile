# SPDX-License-Identifier: GPL-2.0
ccflags-y += -I$(src) -Wno-int-conversion -DCONFIG_ANDROID -DCONFIG_ANDROID_BINDER_IPC

obj-m := kmre-binder.o
kmre-binder-objs := binder.o binder_alloc.o

ifneq ($(KERNELRELEASE),)
KERNELDIR ?= /lib/modules/$(KERNELRELEASE)/build
else
KERNELDIR ?= /lib/modules/$(shell uname -r)/build
endif

PWD := $(shell pwd)

.PHONY: all
all: clean modules #install

.PHONY: modules
modules:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) modules

.PHONY: clean
clean:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) clean
