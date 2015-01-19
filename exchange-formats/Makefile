.PHONY: all clean

DICOM_NANOPB := $(shell cd ../../nanopb;pwd)
DICOM_PBASE_DIR := $(shell pwd)

all: main

include dicom-proto.mk

SRC_DIR := src
SRC := test.c
CFLAGS := -I$(DICOM_NANOPB) -I$(PROTO_DIR)

main: $(PROTOS:.proto=.pb.o) $(NANOPB_SRC:.c=.o) $(SRC:.c=.o)
	gcc -o $@ $^

$(SRC:.c=.o): %.o: $(SRC_DIR)/%.c
	gcc -o $@ -c $< $(CFLAGS)

clean: proto-clean
	rm -fr $(SRC:.c=.o) main