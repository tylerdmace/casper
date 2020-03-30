CCPATH:=$(PREFIX)/bin
AS=i686-elf-as
CC=i686-elf-gcc
ISODIR=iso
GRUBTOOL=grub2-mkrescue
CFLAGS?=-O2
CFLAGS:=$(CFLAGS) -Wall -Wextra

.PHONY: all boot clean iso kernel linker

all: boot kernel linker iso

boot: boot.s
	$(CCPATH)/$(AS) boot.s -o boot.o

kernel: kernel.c
	$(CCPATH)/$(CC) -c kernel.c -o kernel.o -std=gnu99 -ffreestanding

linker: linker.ld
	$(CCPATH)/$(CC) -T linker.ld -o casper.bin -ffreestanding -nostdlib boot.o kernel.o -lgcc

iso:
	mkdir -p $(ISODIR)/boot/grub
	cp casper.bin $(ISODIR)/boot/
	cp grub.cfg $(ISODIR)/boot/grub/
	$(GRUBTOOL) -o casper.iso $(ISODIR)

clean:
	rm -f boot.o
	rm -f kernel.o
	rm -f casper.bin
	rm -f casper.iso
	rm -rf iso
