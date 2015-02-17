all: cleanAll Image_p2 
Image_p2: head Image_p1
	dd bs=512 if=head of=Image skip=8 seek=1
	hexdump Image > Image.txt 
Image_p1: boot 
	dd bs=32 if=boot of=Image skip=1
head: head.o
	ld -x -m elf_i386 -Ttext 0 -o head head.o
	hexdump head > head.txt
head.o: head.s
	as --32 -o head.o head.s
boot: boot.o
	ld86 -0 -s -o boot boot.o
	hexdump boot > boot.txt
boot.o: boot.s
	as86 -0 -a -o boot.o boot.s
cleanAll:
	rm -f Image head.o boot.o
