# ===================================================================================
# Project:  CH32V003 Tiny Invaders
# Author:   Stefan Wagner
# Year:     2023
# URL:      https://github.com/wagiminator    
# ===================================================================================
# Type "make help" in the command line.
# ===================================================================================

# Input and Output File Names
SKETCH   = tiny_invaders.c
TARGET   = tiny_invaders
INCLUDE  = include
LINKER   = linker

# Microcontroller Settings
F_CPU    = 12000000

# Toolchain
PREFIX   = riscv64-unknown-elf
CC       = $(PREFIX)-gcc
OBJCOPY  = $(PREFIX)-objcopy
OBJDUMP  = $(PREFIX)-objdump
OBJSIZE  = $(PREFIX)-size
FLASHER  = ./tools/minichlink -w $(TARGET).bin flash -b
CLEAN    = rm -f *.lst *.obj *.cof *.list *.map *.eep.hex *.o *.d

# Compiler Flags
CFLAGS   = -g -Os -flto -ffunction-sections -static-libgcc -march=rv32ec -mabi=ilp32e
CFLAGS  += -I/usr/include/newlib -I$(INCLUDE) -I. -DF_CPU=$(F_CPU) -nostdlib  -Wall
LDFLAGS  = -T$(LINKER)/ch32v003.ld -Wl,--gc-sections -L$(LINKER) -lgcc
CFILES   = $(SKETCH) $(wildcard $(INCLUDE)/*.c) $(wildcard $(INCLUDE)/*.s)

# Symbolic Targets
help:
	@echo "Use the following commands:"
	@echo "make all       compile and build $(TARGET).elf/.bin/.hex/.asm"
	@echo "make hex       compile and build $(TARGET).hex"
	@echo "make asm       compile and disassemble to $(TARGET).asm"
	@echo "make bin       compile and build $(TARGET).bin"
	@echo "make flash     compile and upload to MCU"
	@echo "make clean     remove all build files"

$(TARGET).elf: $(CFILES)
	@echo "Building $(TARGET).elf ..."
	@$(CC) -o $@ $^ $(CFLAGS) $(LDFLAGS)

$(TARGET).lst: $(TARGET).elf
	@echo "Building $(TARGET).lst ..."
	@$(OBJDUMP) -S $^ > $(TARGET).lst

$(TARGET).map: $(TARGET).elf
	@echo "Building $(TARGET).map ..."
	@$(OBJDUMP) -t $^ > $(TARGET).map

$(TARGET).bin: $(TARGET).elf
	@echo "Building $(TARGET).bin ..."
	@$(OBJCOPY) -O binary $< $(TARGET).bin

$(TARGET).hex: $(TARGET).elf
	@echo "Building $(TARGET).hex ..."
	@$(OBJCOPY) -O ihex $< $(TARGET).hex

$(TARGET).asm: $(TARGET).elf
	@echo "Disassembling to $(TARGET).asm ..."
	@$(OBJDUMP) -d $(TARGET).elf > $(TARGET).asm

all:	$(TARGET).lst $(TARGET).map $(TARGET).bin $(TARGET).hex $(TARGET).asm size

elf:	$(TARGET).elf removetemp size

bin:	$(TARGET).bin removetemp size removeelf

hex:	$(TARGET).hex removetemp size removeelf

asm:	$(TARGET).asm removetemp size removeelf

flash:	$(TARGET).bin size removeelf
	@echo "Uploading to MCU ..."
	$(FLASHER)

clean:
	@echo "Cleaning all up ..."
	@$(CLEAN)
	@rm -f $(TARGET).elf $(TARGET).bin $(TARGET).hex $(TARGET).asm

size:
	@echo "------------------"
	@echo "FLASH: $(shell $(OBJSIZE) -d $(TARGET).elf | awk '/[0-9]/ {print $$1 + $$2}') bytes"
	@echo "SRAM:  $(shell $(OBJSIZE) -d $(TARGET).elf | awk '/[0-9]/ {print $$2 + $$3}') bytes"
	@echo "------------------"

removetemp:
	@echo "Removing temporary files ..."
	@$(CLEAN)

removeelf:
	@echo "Removing $(TARGET).elf ..."
	@rm -f $(TARGET).elf
