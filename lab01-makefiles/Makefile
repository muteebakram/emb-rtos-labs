PICO_TOOLCHAIN_PATH=~/.pico-sdk/toolchain/13_2_Rel1/
CPP=$(PICO_TOOLCHAIN_PATH)/bin/arm-none-eabi-cpp

CC=$(PICO_TOOLCHAIN_PATH)/bin/arm-none-eabi-gcc
AS=$(PICO_TOOLCHAIN_PATH)/bin/arm-none-eabi-as
LD=$(PICO_TOOLCHAIN_PATH)/bin/arm-none-eabi-ld

SRC=main.c second.c
OBJS=$(patsubst %.c, %.o, $(SRC))

.PHONY: all clean

firmware.elf: $(OBJS)
	$(LD) -o $@ $^

%.o: %.s
	$(AS) $< -o $@

main.s: main.i
	$(CC) -S main.i

# main.o: main.s
#	$(AS) main.s -o main.o

main.i: main.c
	$(CPP) main.c > main.i

hello.txt:
	echo "hello world" > hello.txt

all: firmware.elf

clean:
#	rm -rf main.i hello.txt
	rm -rf *.i *.o *.s *.txt *.elf
