# esp32s2-seq

This is not functional yet.

Send commands from [ESP32-S2 Mini](https://www.wemos.cc/en/latest/s2/s2_mini.html) to Novation Launchpad X. Might evolve into a step sequencer one day.

## Building

```
pio run
```

## Hardware

The ESP32-S2 Mini can power the Novation Launchpad X from the USB C port using the VBUS (5V) and GND pins on the ESP32-S2 Mini.

## Flashing

Tested on FreeBSD:

* Connect to USB
* Keep 0 button pressed while pressing RST button to enter firmware upload mode

```
python3 -m pip3 install --upgrade esptool
sudo -E python3 -m esptool --port /dev/ttyU0 erase_flash
sudo -E python3 -m esptool --chip esp32s2 --port /dev/ttyU0 write_flash 0 ~/Downloads/firmware_merged.bin
```

## TODO

* Get the Novation Launchpad X go into Programmer Mode (the light show should then end); why is it not working yet? Not sending to second MIDI interface? Also see https://github.com/touchgadget/esp32-usb-host-demos/issues/11
* Get it to blink some LEDs; why is it not working yet?
* Forward MIDI coming from Novation Launchpad X on the first MIDI interface as Serial MIDI to the instrument, e.g, [MiniDexed](https://github.com/probonopd/MiniDexed/)
* Maybe use https://github.com/TheKikGen/midiXparser
* Implement step sequencer (possibly using existing Arduino code from an existing step sequencer?)

## Documentation

* Novation [Launchpad X Programmer’s reference manual](https://fael-downloads-prod.focusrite.com/customer/prod/s3fs-public/downloads/Launchpad%20X%20-%20Programmers%20Reference%20Manual.pdf)

## Credits

* https://github.com/touchgadget/esp32-usb-host-demos/