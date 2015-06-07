# HalfDuplexHardwareSerial
A modification of the Arduino HardwareSerial library to perform half-duplex communication with the built-in UART in the AVR.

Usage:

```
#include <HalfDuplexHardwareSerial.h>

void setup() {

  // you have to manually set the TX and RX lines of your chosen serial port to INPUT_PULLUP
  // as this is the state they will be in when they are disconnected from the UART
  // you also need to physically link the TX and RX pins in your circuit
  pinMode(0, INPUT_PULLUP);
  pinMode(1, INPUT_PULLUP);

  // for every SerialX object, there is a corresponding HalfDuplexHardwareSerialX object.

  // you will get confusing compilation errors about multiply defined vectors if you make use of 
  // SerialX and it's HalfDuplexHardwareSerialX counterpart in the same sketch


  HalfDuplexHardwareSerial.begin(57600);

  // So don't do this...
  // Serial.begin(57600);

  // But you can still do this:
  Serial1.begin(57600);

}

void loop() {
  // there is no "direction" pin, it stays in receive mode except when outputting.
  HalfDuplexHardwareSerial.print("hello!");
  HalfDuplexHardwareSerial.read();
}
```
