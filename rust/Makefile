BIN ?= target/avr-atmega328p/debug/blink.elf

$(BIN):
	cargo build -Z build-std=core --target avr-atmega328p.json

upload: $(BIN)
	avrdude -D -F -V -c arduino -p ATMEGA328P -P /dev/ttyACM0 -b 115200 \
		-U flash:w:$(BIN):e

clean:
	cargo clean

.PHONY: upload clean
