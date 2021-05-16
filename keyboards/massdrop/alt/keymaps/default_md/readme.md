
```shell
qmk setup --home ~/dev/qmk_firmware
sudo cp /home/hayden/dev/qmk_firmware/util/udev/50-qmk.rules /etc/udev/rules.d/

qmk config user.keyboard=massdrop/alt
# qmk config user.keymap=denhai
qmk config user.keymap=default_md
qmk compile

cd mdloader
sudo ./mdloader_linux --first --download ../massdrop_alt_denhai.bin --restart
```

Note: Made my edits in default_md to make it easier to pull in upstream changes.

One liner:
```shell
qmk compile && cd ~/dev/mdloader && sudo ./mdloader_linux --first --download ~/dev/qmk_firmware/massdrop_alt_default.bin --restart && cd ~/dev/qmk_firmware
```

# Debugging

rules.mk:
```
CONSOLE_ENABLE = yes         # Console for debug
COMMAND_ENABLE = yes         # Commands for debug and configuration
```

Run `sudo hid_listen`.

Press: Left Shift+Right Shift then
* D - for debug mode
  * Outputs hue and rgb changes to console 
* V - for version

Example:
```
$ sudo hid_listen
Waiting for device:
Listening:
debug: on
rgb matrix set hsv [EEPROM]: 85,255,150
```
