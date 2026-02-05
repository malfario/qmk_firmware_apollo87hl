# Install QMK CLI

```
$ uv tool install qmk
$ export QMK_HOME='~/qmk_firmware' # Optional, set the location for `qmk_firmware`
$ qmk setup  # This will clone `qmk/qmk_firmware` and optionally set up your build environment
```

# Compile firmware

```
$ qmk clean
$ qmk compile -kb acheron/apollo/87hlarc2 -km via
```

Command output:

```
Ψ Compiling keymap with gmake -r -R -f builddefs/build_keyboard.mk -s KEYBOARD=acheron/apollo/87hlarc2 KEYMAP=via KEYBOARD_FILESAFE=acheron_apollo_87hlarc2 TARGET=acheron_apollo_87hlarc2_via VERBOSE=false COLOR=true SILENT=false QMK_BIN="qmk"

[...]

arm-none-eabi-gcc (Homebrew ARM GCC 8.5.0_2) 8.5.0
Copyright (C) 2018 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Size before:
   text    data     bss     dec     hex filename
      0   32344       0   32344    7e58 acheron_apollo_87hlarc2_via.bin

Compiling: quantum/via.c                                                                            [OK]
Linking: .build/acheron_apollo_87hlarc2_via.elf                                                     [OK]
Creating binary load file for flashing: .build/acheron_apollo_87hlarc2_via.bin                      [OK]
Creating load file for flashing: .build/acheron_apollo_87hlarc2_via.hex                             [OK]

Size after:
   text    data     bss     dec     hex filename
      0   32344       0   32344    7e58 acheron_apollo_87hlarc2_via.bin

Copying acheron_apollo_87hlarc2_via.bin to qmk_firmware folder                                      [OK]
```

# Flash firmware with QMK CLI

Run `flash` command and enter bootloader (DFU) mode by pressing `Fn-ESC`.

```
$ qmk flash -kb acheron/apollo/87hlarc2 -km via
```

Command output:

```
Flashing for bootloader: stm32-dfu
Bootloader not found. Make sure the board is in bootloader mode. See https://docs.qmk.fm/#/newbs_flashing
Trying again every 0.5s (Ctrl+C to cancel)..........
dfu-util 0.11

Copyright 2005-2009 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2021 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Please report bugs to http://sourceforge.net/p/dfu-util/tickets/

Opening DFU capable USB device...
Device ID 0483:df11
Device DFU version 011a
Claiming USB DFU Interface...
Setting Alternate Interface #0 ...
Determining device status...
DFU state(10) = dfuERROR, status(10) = Device's firmware is corrupt. It cannot return to run-time (non-DFU) operations
Clearing status
Determining device status...
DFU state(2) = dfuIDLE, status(0) = No error condition is present
DFU mode device DFU version 011a
Device returned transfer size 2048
DfuSe interface name: "Internal Flash  "
Downloading element to address = 0x08000000, size = 64520
Erase           [=========================] 100%        64520 bytes
Erase    done.
Download        [=========================] 100%        64520 bytes
Download done.
File downloaded successfully
Submitting leave request...
Transitioning to dfuMANIFEST state
```

# Flash with QMK configurator

+ Install and open QMK Configurator.
+ Press Fn-ESC to enter DFU mode
+ Flash compiled firmware (eg. `qmk_firmware/acheron_apollo_87hlarc2_via.bin`)

