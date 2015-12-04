#
# this makefile is called from the kernel make system. Thus we basically
# add things to "obj-m" here.

ifeq ($(MODE),release)
    ccflags-y = -O2 -DNDEBUG
else
    ccflags-y = -DDEBUG
endif # DEBUG/RELEASE

# CFLAG for testable mode
ifeq ($(IS_TESTABLE),yes)
	ccflags-y = -DTEST
endif

# CFLAGS from the build script
ifdef MOBICORE_CFLAGS
	ccflags-y += $(MOBICORE_CFLAGS)
endif

ccflags-y += -Wall -D__$(PLATFORM)__ -I $(M)
# add our module to kernel.
obj-m += mcDrvModule.o

mcDrvModule-objs := \
	admin.o \
	client.o \
	clientlib.o \
	clock.o \
	fastcall.o \
	logging.o \
	main.o \
	mcp.o \
	mmu.o \
	pm.o \
	scheduler.o \
	session.o \
	user.o

clean:
	rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions \
		Module.markers mcDrvModule.symvers modules.order
