# Micropython TSL2591 module

This is a simple python library for the Adafruit TSL2591 breakout board based on the [Arduino library](https://github.com/adafruit/Adafruit_TSL2591_Library) from Adafruit. [python-tsl2591](https://github.com/maxlklaxl/python-tsl2591) was developed to work on a Raspberry PI. I then forked it to create a [Micropython](http://www.micropython.org) version. There were two changes from the original:

1. Micropython does not provide an sbus api, so sbus was emulated on top of the lower-level I2C library it does provide.
2. The ESP8266 and other chips are severely memory limited. With the Raspberry Pi version, even importing the tsl2591 moduled cause it to run out of memory on the ESP8266. The code was simplified were possible and all the comments stripped out.

# INFO

Enabeling I2C on the Raspberry Pi. You should be fine by following the instruction on [Adafruit](https://learn.adafruit.com/adafruits-raspberry-pi-lesson-4-gpio-setup/configuring-i2c).

In the last step ('Testing I2C') you should see at least one connected device, your TSL2591 (most likely at 0x29 ).




## Installing ##

To install the python module download this repository and run:

```
python setup.py install
```



## Quickstart ##


```
import tsl2591

tsl = tsl2591.Tsl2591()  # initialize
full, ir = tsl.get_full_luminosity()  # read raw values (full spectrum and ir spectrum)
lux = tsl.calculate_lux(full, ir)  # convert raw values to lux
print lux, full, ir
```




## License ##

Python files in this repository are released under the [MIT license](LICENSE.md).
