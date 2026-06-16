# 4.0-inch-Arduino-Display-Mega2560-NT35510
LCDWIKI_NT35510_Mega_Adapted Library

LCDWIKI_NT35510_Mega_Adapted 4.0inch Arduino Display-Mega2560 NT35510 Adapted library for the 4.0" 800x480 Arduino display with NT35510 controller on Arduino Mega 2560.Based on the official library from lcdwiki.com 4.0inch_Arduino_Display-Mega2560_NT35510, but modified to work with Adafruit_GFX functions and custom fonts.


What's improved vs original library1. 

Adafruit_GFX compatibilityFunctions like 

drawLine,

drawRect,

fillCircle, 

setCursor, 

print work the same as Adafruit_GFX Easy porting from other displays without rewriting code MyGFX class inherits from Adafruit_GFX2. Custom font supportFull support for Adafruit_GFX font format:

FreeMono,

FreeSans,

FreeSerif 

Allstyles included: 

Regular, 

Bold, 

Italic, 

Oblique, 

BoldOblique + pixel fonts Org_01,

TomThumb,

PicopixelSet font with tft.setFont(&FreeSans18pt7b)3.

Optimized for 800x480 Faster fill operations for large areas Correct screen rotation with setRotation() Fixed NT35510 initialization issues on Mega 2560





```
LCD RS/CS  -> 38/39  
LCD RST    -> 40
LCD WR/RD  -> 41/43
LCD DB0-DB15 -> 22-37
```


Quick example:


```
#include <LCDWIKI_GUI.h>
#include <LCDWIKI_KBV.h>
#include "MyGFX.h"
#include <Fonts/FreeSans18pt7b.h>

LCDWIKI_KBV mar_TFT(NT35510,40,38,39,43,41);
MyGFX tft(&mar_TFT);

void setup() {
  tft.begin();
  tft.fillScreen(BLACK);
  tft.setFont(&FreeSans18pt7b);
  tft.setTextColor(WHITE);
  tft.setCursor(100, 100);
  tft.print("Hello 800x480");
}
```


Important note about fonts:

Arduino Mega 2560 has a 64KB limit per FLASH segment. You cannot compile all 52 GFX fonts at once - you'll get "value too large for field of 2 bytes" error. Use max 8-10 fonts per sketch for testing. For final project keep only 3-4 fonts you actually need.



Installation:


1: Copy the whole folder to Arduino/libraries/

2: Arduino IDE: Tools -> Board -> Arduino Mega 2560

3: Open example font_demo_800x480.ino
