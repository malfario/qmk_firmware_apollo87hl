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
Ψ Compiling keymap with gmake -r -R -f builddefs/build_keyboard.mk -s KEYBOARD=acheron/apollo/87hlarc2 KEYMAP=via KEYBOARD_FILESAFE=acheron_apollo_87hlarc2 TARGET=acheron_apollo_87hlarc2_via VERBOSE=false COLOR=true SILENT=false QMK_BIN="qmk"

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

# Flash firmware

+ Install and open QMK Configurator.
+ Press Fn-ESC to enter keyboard in DFU mode
+ Flash compiled firmware (eg. `qmk_firmware/acheron_apollo_87hlarc2_via.bin`)

