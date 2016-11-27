# teensy 3.6 hardware configuration

Teensy 3.6 with two SSD1306 OLED displays (128x64), connected via I2C, and a MicroSD card.

*	One OLED display connected to (SCL0, SDA0), used for VM console output.
*	One OLED display connected to (SCL1, SDA1), used for VM internal status.
*	Individual pull-up resistors connected to each of SCL0, SDA0, SCL1, SDA1.
*	MicroSD card, for loading compiled object files.
  