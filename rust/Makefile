BIN ?= target/avr-atmega328p/debug/blink.elf

$(BIN):
	# Rust -> ELF
	cargo build -Z build-std=core --target avr-atmega328p.json
	# ELF -> HEX
	avr-objcopy -O ihex -R .eeprom $(BIN) $(BIN).hex

upload: $(BIN)
	# HEX -> Arduino
	avrdude -F -V -c arduino -p ATMEGA328P -P /dev/ttyACM0 -b 115200 \
	        -U flash:w:$(BIN).hex

clean:
	cargo clean

.PHONY: upload clean
