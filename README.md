# Blink Analysis

Most Arduino tutorials take the IDE as a given.
This makes sense for ease of use, but what is really behind those "Verify" and "Upload" buttons?
Instead of building complex software on top of an IDE, this project goes in the opposite direction: how does the simplest possible Arduino program work on a deeper level?

Using 4 languages as examples:

- Arduino IDE (flavored C++)
- Bare C
- AVR Assembly
- Rust

## Arduino IDE
Just the builitn [Basic Examples](http://www.arduino.cc/en/Tutorial/Blink).
Not included here, there's nothing to change.

## C
Adaption of builtin example, build steps come directrly from building in Arduino IDE with verbose output.


## AVR Assembly
Gold mine in [this small blog post](http://www.dwelch.com/arduino/), adapted from ATmega168 into ATmega328p.
[This lecture](http://www.avr-asm-tutorial.net/avr_en/micro_beginner/3_Led_Blinking/3_Led_Blinking.html) gives more theory, architecture, and timing information.

## Rust
This is almost entirely [avr-rust's blink example](https://github.com/avr-rust/blink), however this example didn't work immediately (for me at least).
The missing pieces came from a blog post on [creativecoder](https://creativcoder.dev/rust-on-arduino-uno) and brute force.
