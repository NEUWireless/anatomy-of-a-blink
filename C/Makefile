BIN ?= blink

# compile straight to .hex
$(BIN).hex: $(BIN).c
	# C -> ELF
	avr-gcc -Os -DF_CPU=16000000UL -mmcu=atmega328p \
	        -o $(BIN) $(BIN).c
	# ELF -> HEX
	avr-objcopy -O ihex -R .eeprom $(BIN) $(BIN).hex

# compile to .hex but emit assembly
$(BIN).asm: $(BIN).c
	# C -> AVR assembly
	avr-gcc -Os -DF_CPU=16000000UL -mmcu=atmega328p \
	        -c -S -o $(BIN).asm $(BIN).c
	# AVR assembly -> object file
	avr-as -mmcu=avr5 -mgcc-isr -mno-skip-bug \
	       -o $(BIN).o $(BIN).asm
	# object file -> ELF
	avr-gcc -mmcu=atmega328p $(BIN).o -o $(BIN)
	# ELF -> HEX
	avr-objcopy -O ihex -R .eeprom $(BIN) $(BIN).hex

upload: $(BIN).hex
	# HEX -> Arduino
	avrdude -F -V -c arduino -p ATMEGA328P -P /dev/ttyACM0 -b 115200 \
	        -U flash:w:$(BIN).hex

clean:
	rm -f *.o *.asm *.hex $(BIN)

.PHONY: upload clean
