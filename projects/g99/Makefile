AS=/opt/ti990/bin/asm990
LD=/opt/ti990/bin/lnk990
HEXDUMP=hexdump

include sources.mk

TARGET=$(notdir $(CURDIR))

AS_FLAGS= -g -l $(BIN_DIR)/$(TARGET).lst
LD_FLAGS= -a -m $(BIN_DIR)/$(TARGET).map -C 6000
HEXDUMP_FLAGS= -C

BIN_DIR=bin
SRC_DIR=src
INC_DIR=inc
CFG_DIR=cfg

OBJS = $(patsubst $(SRC_DIR)/%.asm, $(BIN_DIR)/%.obj, $(SRCS))

.PHONY = all, link, build, clean, dump

all: link

$(BIN_DIR)/%.obj : $(SRC_DIR)/%.asm
	$(AS) $(AS_FLAGS) -o $@ $<

link: build
	$(LD) $(LD_FLAGS) -o $(BIN_DIR)/g99.bin $(BIN_DIR)/$(OBJS)

build: $(OBJS)

dump: link
	$(HEXDUMP) $(HEXDUMP_FLAGS) $(BIN_DIR)/g99.bin

clean:
	rm -rf $(BIN_DIR)/*
