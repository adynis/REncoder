# What is REncoder ?

REncoder is a simple Rotary Encoder and Switch Button implementation for Adruino and compatible boards.
While working on a Home Automation project, I got in the need of using an Rotary Encoder with a builtin Switch. 

At first, I was thinking: *of course there are tons of such libraries !*, so i've start searching. Soon I just realized that while there are some libraries here and there that practically are doing that in one way or the other, none of them really worked good (if at all!) on the boards I needed them to work: the Arduino UNO, Arduino MEGA and the Seeeduino XIAO. 

In addition, I wanted to be able to control some things, like if IRQs must be used or not, if the push of the switch is detected continuously, to set limits on the maximum and minimum value of the encoder rotation, and so on. While some of these features were (partially) available in some other libraries, I wasn't satisfied with the results, so it was the time to get to work and create a such library. A few hours and two cups of caffe later, I come up with this library. Feel free to use it if you need it.

# How to use REncoder

Rencoder is basicaly just another Arduino library. To use it, you have multiple choices, such as:
- download it as zip and install it on your Arduino IDE by using the *"Sketch > Include Library > Add .ZIP Library"* menu;
- download the souce code from here and then copy / paste the header (.h) and implementation files (.cpp) files somewhere on your project folder then use ```#include "path-to-library-folder"``` to load them on your sketch;
- use PlatformIO IDE and refer the library on your project.
- ... or imagine something by yourself and do it so ...

# Configure the library

This library is configurable. The configuration parameters are available in the ```REncoderConfig.h``` file. Due to the way on how the compilation works, you can't simply just define these parameters as part of your own code, i.e., inside your sketch file. The parameters affects the compilation, since the code is compiled based on these parameters. The main reason is to keep the usage of the RAM / FLASH resources as low as possible...these are anyway very limited in some boards.

The following parameters / flags are available:

- ```RENCODER_ENABLE_SWITCH```: enable or disable the switch on the rotary encoder. This only works of course if and only if a switch is builtin the rotary encoder. Alternatively, you can use a button in combination with a simple rotary encoder.
- ```RENCODER_ENABLE_SWITCH_IRQ```: enable or disable the IRQ for the switch. When using this, make sure that the GPIO connected to the switch / button pin is one that supports interrupts (IRQ). Otherwise, it will either not work at all, or worst, it will make your program act strange...unpredictible.
- ```RENCODER_ENABLE_SWITCH_SOFTWARE_DEBOUNCING```: enable or disable software debouncing for the switch. While this may be an alternative to real debouncing, it also uses additional resources and it is not optimal when the switch ages, and debouncing becomes harder to be done in the software. Alternatively, use a 01.uF / 100nF capacitor between the SW (or the button) pin and the GND.


