# ZMK config for beekeeb Toucan Keyboard

[The beekeeb Toucan Keyboard](https://beekeeb.com/toucan-keyboard/) is a wireless split 42-key column‑stagger keyboard that a display and a trackpad, with an aggressive stagger on the pinky columns.

# License

The code in this repo is available under the MIT license.

The included shield nice_view_gem is modified from https://github.com/M165437/nice-view-gem licensed under the MIT License.

ZMK code snippets are taken from the ZMK documentation under the MIT license.

The embedded font QuinqueFive is designed by GGBotNet, licensed under under the SIL Open Font License, Version 1.1.

# Setup
```bash
docker volume create --driver local -o o=bind -o type=none -o device="D:/Repository/zmk/toucan-config" zmk-config
docker volume create --driver local -o o=bind -o type=none -o device="D:/Repository/zmk/modules" zmk-modules

```
# Build
```bash
west build -p -b seeeduino_xiao_ble -S studio-rpc-usb-uart -d /build/left -- -DSHIELD="toucan_left rgbled_adapter nice_view_gem" -DZMK_EXTRA_MODULES="/workspaces/zmk-config;/workspaces/zmk-modules/zmk-rgbled-widget;/workspaces/zmk-modules/cirque-input-module" -DZMK_CONFIG="/workspaces/zmk-config/config"

west build -p -b seeeduino_xiao_ble -S studio-rpc-usb-uart -d /build/right -- -DSHIELD="toucan_right rgbled_adapter" -DZMK_EXTRA_MODULES="/workspaces/zmk-config;/workspaces/zmk-modules/zmk-rgbled-widget;/workspaces/zmk-modules/cirque-input-module" -DZMK_CONFIG="/workspaces/zmk-config/config"

west build -p -b seeeduino_xiao_ble -S studio-rpc-usb-uart -d /build/reset -- -DSHIELD="settings_reset" -DZMK_EXTRA_MODULES="/workspaces/zmk-config;/workspaces/zmk-modules/zmk-rgbled-widget;/workspaces/zmk-modules/cirque-input-module" -DZMK_CONFIG="/workspaces/zmk-config/config"
```