# esplorative-idiot

esplorative-idiot is a throwaway repository to test the LoRa technology from
within [zephyr].

It intends to build a firmware to run on Heltec [WiFi LoRa 32 v2] boards.

## FETCH, BUILD AND FLASH

Create and enter the workspace directory:

	mkdir esplorative-workspace
	cd esplorative-workspace

Fetch the sources down to the workspace:

	west init -m git@github.com:idiot-prototypes/esplorative-idiot
	west update

Build and flash the sample from the [zephyr] source tree:

	west build -b heltec_wifi_lora32_v2 zephyr/samples/subsys/shell/shell_module/ -- -DDTC_OVERLAY_FILE=$PWD/esplorative-idiot/heltec_wifi_lora32_v2.overlay -DCONF_FILE=$PWD/esplorative-idiot/prj.conf
	west flash

## PREREQUISITE

### CMAKE PACKAGE

Install the Zephyr [CMake package] using [west] `zephyr-export`:

	west zephyr-export

### TOOLCHAIN

Install the [toolchain] by extracting the archive to the home directory
`~/.espressif/tools/zephyr`.

Example on Linux x86_64:

	mkdir -p ~/.espressif/tools/zephyr
	curl -s https://dl.espressif.com/dl/xtensa-esp32-elf-gcc8_4_0-esp-2020r3-linux-amd64.tar.gz | tar xvzf - -C ~/.espressif/tools/zephyr

### SHELL COMPLETION (OPTIONAL)

Eventually, install the [shell completion] script using [west] `completion`,
and relog then (or `source ~/.local/share/bash-completion/completions/west`).

Example for bash:

	mkdir -p ~/.local/share/bash-completion/completions
	west completion bash >~/.local/share/bash-completion/completions/west

## BUGS

Report bugs at *https://github.com/idiot-prototypes/esplorative-idiot/issues*

## AUTHOR

Written by Gaël PORTAY *gael.portay@gmail.com*

## COPYRIGHT

Copyright (c) 2022 Gaël PORTAY

This program is free software: you can redistribute it and/or modify it under
the terms of the GNU Lesser General Public License as published by the Free
Software Foundation, either version 2.1 of the License, or (at your option) any
later version.

[west]: https://github.com/zephyrproject-rtos/west
[zephyr]: https://github.com/zephyrproject-rtos/zephyr
[WiFi LoRa 32 v2]: https://heltec.org/project/wifi-lora-32/
[CMake package]: https://docs.zephyrproject.org/latest/build/zephyr_cmake_package.html#zephyr-cmake-package-export-west
[toolchain]: https://docs.espressif.com/projects/esp-idf/en/v4.2/esp32/api-guides/tools/idf-tools.html#xtensa-esp32-elf
[shell completion]: https://docs.zephyrproject.org/latest/develop/west/install.html#enabling-shell-completion
