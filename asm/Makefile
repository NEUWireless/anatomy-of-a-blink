BIN ?= blink

$(BIN).hex: $(BIN).asm
	# AVR Assembly -> Object file
	avr-as $(BIN).asm -o $(BIN).o
	# Object file -> ELF
	avr-ld -Ttext 0 -nostdlib -nostartfiles  $(BIN).o -o $(BIN).elf
	# ELF -> HEX
	avr-objcopy -O ihex $(BIN).elf $(BIN).hex

upload: $(BIN).hex
	# HEX -> Arduino
	avrdude -F -V -c arduino -p ATMEGA328P -P /dev/ttyACM0 -b 115200 \
	        -U flash:w:$(BIN).hex

clean:
	rm -f *.o *.elf *.hex

.PHONY: clean
