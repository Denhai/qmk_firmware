
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
