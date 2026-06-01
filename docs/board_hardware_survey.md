# xiaozhi-esp32 硬件版本穷举调研

生成时间：2026-06-01。

## 调研口径

- 范围：`main/boards/**/config.json` 对应的板级目录。
- 依据：`config.json`、同目录 `config.h`、板级 `*.cc/*.h` 和 README 中可识别的硬件初始化代码。
- 注意：本表是源码视角的硬件能力归纳；若某块板子的 README 或源码没有清晰暴露外设，则标为“未明确识别”，不代表硬件一定没有该能力。
- 配置异常：freenove-esp32s3-display-2.8-lcd/config.json 标准 JSON 解析失败：Expected ',' or ']' after array element in JSON at position 338 (line 10 column 17)；已用正则提取 target/build name 纳入统计。

## 总览

- 板级目录/配置数量：125 个。
- 芯片平台分布：esp32 6 个，esp32c3 9 个，esp32c5 3 个，esp32c6 7 个，esp32p4 6 个，esp32s3 94 个。
- 联网形态：WiFi 106 个，WiFi + 4G/蜂窝 15 个，4G/蜂窝 3 个，未明确识别 1 个。
- 可识别带屏显示：102 个；可识别摄像头：29 个；可识别触摸：71 个；可识别参考声道/AEC：55 个。

## 硬件版本全量清单

| # | 板级目录 | 芯片 | 构建名 | 简要功能定位 | 联网 | 音频 | 显示 | 其他外设 |
|---:|---|---|---|---|---|---|---|---|
| 1 | `atommatrix-echo-base` | esp32 | atommatrix-echo-base | WiFi 联网 | WiFi | ES8311 音频 | 无/未明确识别 | LED/灯效 |
| 2 | `bread-compact-esp32` | esp32 | bread-compact-esp32, bread-compact-esp32-128x32 | 触摸交互、蜂窝联网 | ML307/4G + WiFi | 无外置 codec/I2S 简化音频 | 128x32；Oled；NoDisplay | 触摸；LED/灯效 |
| 3 | `bread-compact-esp32-lcd` | esp32 | bread-compact-esp32-lcd | 带屏显示、触摸交互、蜂窝联网 | ML307/4G + WiFi | 无外置 codec/I2S 简化音频 | 240x320；SpiLcd | 触摸；LED/灯效 |
| 4 | `esp32-cgc` | esp32 | esp32-cgc | 带屏显示、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 240x320；SpiLcd | 基础语音交互 |
| 5 | `esp32-cgc-144` | esp32 | esp32-cgc-144 | 带屏显示、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 128x128；SpiLcd | 电池/电源管理 |
| 6 | `waveshare/esp32-touch-lcd-3.5` | esp32 | esp32-touch-lcd-3.5 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频；参考声道/AEC | 480x320；SpiLcd | 触摸；电池/电源管理；LED/灯效 |
| 7 | `esp-hi` | esp32c3 | esp-hi | 带屏显示、触摸交互、WiFi 联网、运动控制 | WiFi | 未明确识别 | 160x80 | 触摸；电池/电源管理；舵机/运动控制；LED/灯效 |
| 8 | `kevin-c3` | esp32c3 | kevin-c3 | WiFi 联网 | WiFi | ES8311 音频 | 无/未明确识别 | LED/灯效 |
| 9 | `lichuang-c3-dev` | esp32c3 | lichuang-c3-dev | 带屏显示、WiFi 联网 | WiFi | ES8311 音频；参考声道/AEC | 320x240；SpiLcd | LED/灯效 |
| 10 | `magiclick-c3` | esp32c3 | magiclick-c3 | 带屏显示、WiFi 联网 | WiFi | ES8311 音频 | 128x128；SpiLcd | 电池/电源管理；LED/灯效 |
| 11 | `magiclick-c3-v2` | esp32c3 | magiclick-c3-v2 | 带屏显示、WiFi 联网 | WiFi | ES8311 音频 | 128x128；SpiLcd | 电池/电源管理；LED/灯效 |
| 12 | `surfer-c3-1.14tft` | esp32c3 | surfer-c3-1.14tft | 带屏显示、WiFi 联网 | WiFi | ES8311 音频；参考声道/AEC | 240x135；SpiLcd | 电池/电源管理；LED/灯效 |
| 13 | `xmini-c3` | esp32c3 | xmini-c3 | WiFi 联网 | WiFi | ES8311 音频 | 128x64；Oled；NoDisplay | 电池/电源管理；LED/灯效 |
| 14 | `xmini-c3-4g` | esp32c3 | xmini-c3-4g | 蜂窝联网 | ML307/4G | ES8311 音频 | 128x64；Oled；NoDisplay | 电池/电源管理；LED/灯效 |
| 15 | `xmini-c3-v3` | esp32c3 | xmini-c3-v3 | WiFi 联网 | WiFi | ES8311 音频 | 128x64；Oled；NoDisplay | 电池/电源管理；LED/灯效 |
| 16 | `esp-sensairshuttle` | esp32c5 | esp-sensairshuttle | 带屏显示、触摸交互、WiFi 联网 | WiFi | 未明确识别 | 284x240；SpiLcd | 触摸；电池/电源管理；LED/灯效 |
| 17 | `esp-spot` | esp32c5 | esp-spot-c5 | WiFi 联网 | WiFi | ES8311 音频；参考声道/AEC | 无/未明确识别 | 电池/电源管理；LED/灯效 |
| 18 | `movecall-moji2-esp32c5` | esp32c5 | movecall-moji2-esp32c5 | 带屏显示、WiFi 联网 | WiFi | ES8311 音频 | 360x360；SpiLcd | 电池/电源管理；LED/灯效 |
| 19 | `waveshare/esp32-c6-lcd-1.69` | esp32c6 | esp32-c6-lcd-1.69 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频 | 240x280；SpiLcd | 触摸；电池/电源管理；LED/灯效 |
| 20 | `waveshare/esp32-c6-touch-amoled-1.32` | esp32c6 | esp32-c6-touch-amoled-1.32 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频 | SpiLcd；Amoled | 触摸；电池/电源管理；LED/灯效 |
| 21 | `waveshare/esp32-c6-touch-amoled-1.43` | esp32c6 | esp32-c6-touch-amoled-1.43 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | SpiLcd；Amoled | 触摸；LED/灯效 |
| 22 | `waveshare/esp32-c6-touch-amoled-1.8` | esp32c6 | esp32-c6-touch-amoled-1.8 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频 | 368x448；SpiLcd；Amoled | 触摸；电池/电源管理；LED/灯效 |
| 23 | `waveshare/esp32-c6-touch-amoled-2.06` | esp32c6 | esp32-c6-touch-amoled-2.06 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 410x502；SpiLcd；Amoled | 触摸；电池/电源管理；LED/灯效 |
| 24 | `waveshare/esp32-c6-touch-amoled-2.16` | esp32c6 | esp32-c6-touch-amoled-2.16 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | SpiLcd；Amoled | 触摸；电池/电源管理；LED/灯效 |
| 25 | `waveshare/esp32-c6-touch-lcd-1.83` | esp32c6 | esp32-c6-touch-lcd-1.83 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 240x284；SpiLcd | 触摸；电池/电源管理 |
| 26 | `esp-p4-function-ev-board` | esp32p4 | esp-p4-function-ev-board | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频 | MipiLcd | 摄像头；触摸；电池/电源管理 |
| 27 | `m5stack-tab5` | esp32p4 | m5stack-tab5 | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | 参考声道/AEC | 720x1280；MipiLcd | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 28 | `waveshare/esp32-p4-nano` | esp32p4 | esp32-p4-nano-10.1-a | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频 | 800x1280；MipiLcd | 摄像头；触摸；电池/电源管理 |
| 29 | `waveshare/esp32-p4-wifi6-touch-lcd` | esp32p4 | esp32-p4-wifi6-touch-lcd-4b, esp32-p4-wifi6-touch-lcd-4.3, esp32-p4-wifi6-touch-lcd-7b, esp32-p4-wifi6-touch-lcd-3.4c, esp32-p4-wifi6-touch-lcd-4c, esp32-p4-wifi6-touch-lcd-7, esp32-p4-wifi6-touch-lcd-8, esp32-p4-wifi6-touch-lcd-10.1 | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | (720)x(720)；MipiLcd | 摄像头；触摸；电池/电源管理 |
| 30 | `waveshare/esp32-p4-wifi6-touch-lcd-3.5` | esp32p4 | esp32-p4-wifi6-touch-lcd-3.5 | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频；参考声道/AEC | (320)x(480)；SpiLcd | 摄像头；触摸 |
| 31 | `wireless-tag-wtp4c5mp07s` | esp32p4 | wireless-tag-wtp4c5mp07s | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频；参考声道/AEC | 1024x600；MipiLcd | 触摸；电池/电源管理；LED/灯效 |
| 32 | `aipi-lite` | esp32s3 | aipi-lite | 带屏显示、WiFi 联网 | WiFi | ES8311 音频 | 128x128；SpiLcd | 电池/电源管理；LED/灯效 |
| 33 | `atk-dnesp32s3` | esp32s3 | atk-dnesp32s3 | 视觉/摄像头、带屏显示、WiFi 联网 | WiFi | ES8388 音频 | 320x240；SpiLcd | 摄像头；LED/灯效 |
| 34 | `atk-dnesp32s3-box` | esp32s3 | atk-dnesp32s3-box | 带屏显示、WiFi 联网 | WiFi | ES8311 音频；无外置 codec/I2S 简化音频 | 320x240；SpiLcd | LED/灯效 |
| 35 | `atk-dnesp32s3-box0` | esp32s3 | atk-dnesp32s3-box0 | 带屏显示、WiFi 联网 | WiFi | ES8311 音频 | 240x240；SpiLcd | 电池/电源管理；LED/灯效 |
| 36 | `atk-dnesp32s3-box2-4g` | esp32s3 | atk-dnesp32s3-box2-4g | 带屏显示、WiFi 联网 | 双网络 + WiFi | ES8389 音频 | 240x320；SpiLcd | 电池/电源管理 |
| 37 | `atk-dnesp32s3-box2-wifi` | esp32s3 | atk-dnesp32s3-box2-wifi | 带屏显示、WiFi 联网 | WiFi | ES8389 音频 | 240x320；SpiLcd | 电池/电源管理 |
| 38 | `atk-dnesp32s3-box3` | esp32s3 | atk-dnesp32s3-box3 | 视觉/摄像头、带屏显示、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 320x240；SpiLcd | 摄像头；电池/电源管理；LED/灯效 |
| 39 | `atom-echos3r` | esp32s3 | atom-echos3r | WiFi 联网 | WiFi | ES8311 音频；参考声道/AEC | 无/未明确识别 | LED/灯效 |
| 40 | `atoms3-echo-base` | esp32s3 | atoms3-echo-base | 带屏显示、WiFi 联网 | WiFi | ES8311 音频；参考声道/AEC | 128x128；SpiLcd | LED/灯效 |
| 41 | `atoms3r-cam-m12-echo-base` | esp32s3 | atoms3r-cam-m12-echo-base | 视觉/摄像头、WiFi 联网 | WiFi | ES8311 音频；参考声道/AEC | 无/未明确识别 | 摄像头；电池/电源管理；LED/灯效 |
| 42 | `atoms3r-echo-base` | esp32s3 | atoms3r-echo-base | 带屏显示、WiFi 联网 | WiFi | ES8311 音频；参考声道/AEC | 128x128；SpiLcd | LED/灯效 |
| 43 | `bread-compact-ml307` | esp32s3 | bread-compact-ml307, bread-compact-ml307-128x64 | 触摸交互、蜂窝联网 | 双网络 + ML307/4G + WiFi | 无外置 codec/I2S 简化音频 | 128x32；Oled；NoDisplay | 触摸；LED/灯效 |
| 44 | `bread-compact-nt26` | esp32s3 | bread-compact-nt26 | 触摸交互、蜂窝联网 | NT26/4G | 无外置 codec/I2S 简化音频 | 128x32；Oled；NoDisplay | 触摸；LED/灯效 |
| 45 | `bread-compact-wifi` | esp32s3 | bread-compact-wifi, bread-compact-wifi-128x64 | 触摸交互、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 128x32；Oled；NoDisplay | 触摸；LED/灯效 |
| 46 | `df-k10` | esp32s3 | df-k10 | 视觉/摄像头、带屏显示、WiFi 联网 | WiFi | 参考声道/AEC | 240x320；SpiLcd | 摄像头；电池/电源管理；LED/灯效 |
| 47 | `df-s3-ai-cam` | esp32s3 | df-s3-ai-cam | 视觉/摄像头、触摸交互、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 无/未明确识别 | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 48 | `doit-s3-aibox` | esp32s3 | doit-s3-aibox | 触摸交互、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 无/未明确识别 | 触摸；LED/灯效 |
| 49 | `du-chatx` | esp32s3 | du-chatx | 带屏显示、触摸交互、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 128x160；SpiLcd | 触摸；电池/电源管理；LED/灯效 |
| 50 | `electron-bot` | esp32s3 | electron-bot | 带屏显示、触摸交互、WiFi 联网、运动控制 | WiFi | 无外置 codec/I2S 简化音频 | 240x240；SpiLcd | 触摸；电池/电源管理；舵机/运动控制；LED/灯效 |
| 51 | `esp-box` | esp32s3 | esp-box | 带屏显示、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 320x240；SpiLcd | LED/灯效 |
| 52 | `esp-box-3` | esp32s3 | esp-box-3 | 带屏显示、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 320x240；SpiLcd | LED/灯效 |
| 53 | `esp-box-lite` | esp32s3 | esp-box-lite | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 320x240；SpiLcd | 触摸；LED/灯效 |
| 54 | `esp-s3-lcd-ev-board` | esp32s3 | esp-s3-lcd-ev-board-1p4, esp-s3-lcd-ev-board-1p5 | 视觉/摄像头、带屏显示、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 480x480；RgbLcd | 摄像头；电池/电源管理；LED/灯效 |
| 55 | `esp-s3-lcd-ev-board-2` | esp32s3 | esp-s3-lcd-ev-board-2 | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 800x480；RgbLcd | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 56 | `esp-sparkbot` | esp32s3 | esp-sparkbot | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网、运动控制 | WiFi | ES8311 音频 | 240x240；SpiLcd | 摄像头；触摸；电池/电源管理；舵机/运动控制；LED/灯效 |
| 57 | `esp-vocat` | esp32s3 | esp-vocat | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 360x360；SpiLcd | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 58 | `esp32s3-korvo2-v3` | esp32s3 | esp32s3-korvo2-v3 | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 280x240；SpiLcd | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 59 | `esp32s3-korvo2-v3-rndis` | esp32s3 | esp32s3-korvo2-v3-rndis | 视觉/摄像头、带屏显示、触摸交互 | 未明确识别 | ES8311+ES7210/Box 音频链路；参考声道/AEC | 280x240；SpiLcd | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 60 | `freenove-esp32s3-display-2.8-lcd` | esp32s3 | freenove-esp32s3-display-2.8-lcd | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频 | 320x240；SpiLcd | 触摸；LED/灯效 |
| 61 | `genjutech-s3-1.54tft` | esp32s3 | genjutech-s3-1.54tft | 带屏显示、WiFi 联网 | WiFi | ES8311 音频 | 240x240；SpiLcd | 电池/电源管理；LED/灯效 |
| 62 | `hu-087` | esp32s3 | hu-087 | 触摸交互、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 128x64；Oled；NoDisplay | 触摸；电池/电源管理 |
| 63 | `jiuchuan-s3` | esp32s3 | jiuchuan-s3 | 带屏显示、WiFi 联网 | WiFi | ES8311 音频；参考声道/AEC | 240x296；SpiLcd | 电池/电源管理；LED/灯效 |
| 64 | `kevin-box-2` | esp32s3 | kevin-box-2 | 蜂窝联网 | 双网络 + ML307/4G + WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 128x64；Oled；NoDisplay | 电池/电源管理；LED/灯效 |
| 65 | `kevin-sp-v4-dev` | esp32s3 | kevin-sp-v4-dev | 视觉/摄像头、带屏显示、蜂窝联网 | ML307/4G + WiFi | ES8311 音频 | 240x280；SpiLcd | 摄像头；LED/灯效 |
| 66 | `kevin-yuying-313lcd` | esp32s3 | kevin-yuying-313lcd | 带屏显示、WiFi 联网 | WiFi | ES8311 音频 | 376x960；RgbLcd | LED/灯效 |
| 67 | `labplus-ledong-v2` | esp32s3 | labplus-ledong-v2 | 带屏显示、WiFi 联网 | WiFi | ES8388 音频 | 320x172；SpiLcd | LED/灯效 |
| 68 | `labplus-mpython-v3` | esp32s3 | labplus-mpython-v3 | 带屏显示、WiFi 联网 | WiFi | ES8388 音频 | 320x172；SpiLcd | LED/灯效 |
| 69 | `lceda-course-examples/eda-robot-pro` | esp32s3 | eda-robot-pro | 触摸交互、WiFi 联网、运动控制 | WiFi | 无外置 codec/I2S 简化音频 | 128x64；Oled；NoDisplay | 触摸；舵机/运动控制；LED/灯效 |
| 70 | `lceda-course-examples/eda-super-bear` | esp32s3 | eda-super-bear | 触摸交互、WiFi 联网、运动控制 | WiFi | 无外置 codec/I2S 简化音频 | NoDisplay | 触摸；电池/电源管理；舵机/运动控制；LED/灯效 |
| 71 | `lceda-course-examples/eda-tv-pro` | esp32s3 | eda-tv-pro | 带屏显示、触摸交互、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 240x240；SpiLcd | 触摸；LED/灯效 |
| 72 | `lichuang-dev` | esp32s3 | lichuang-dev | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；自定义音频；参考声道/AEC | 320x240；SpiLcd | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 73 | `lilygo-t-cameraplus-s3` | esp32s3 | lilygo-t-cameraplus-s3, lilygo-t-cameraplus-s3_v1_2 | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | 参考声道/AEC | LCD_WIDTHxLCD_HEIGHT；SpiLcd | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 74 | `lilygo-t-circle-s3` | esp32s3 | lilygo-t-circle-s3 | 带屏显示、触摸交互、WiFi 联网、旋钮/编码器 | WiFi | 参考声道/AEC | LCD_WIDTHxLCD_HEIGHT；SpiLcd | 触摸；电池/电源管理；旋钮/编码器；LED/灯效 |
| 75 | `lilygo-t-display-s3-pro-mvsrlora` | esp32s3 | lilygo-t-display-s3-pro-mvsrlora | 带屏显示、触摸交互、WiFi 联网、运动控制 | WiFi | 参考声道/AEC | LCD_WIDTHxLCD_HEIGHT；SpiLcd | 触摸；电池/电源管理；舵机/运动控制；LED/灯效 |
| 76 | `m5stack-cardputer-adv` | esp32s3 | m5stack-cardputer-adv | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频 | 240x135；SpiLcd | 触摸；LED/灯效 |
| 77 | `m5stack-core-s3` | esp32s3 | m5stack-core-s3 | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | 参考声道/AEC | 320x240；SpiLcd | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 78 | `magiclick-2p4` | esp32s3 | magiclick-2p4 | 带屏显示、WiFi 联网 | WiFi | ES8311 音频 | 128x128；SpiLcd | 电池/电源管理；LED/灯效 |
| 79 | `magiclick-2p5` | esp32s3 | magiclick-2p5 | 带屏显示、蜂窝联网 | 双网络 + ML307/4G + WiFi | ES8311 音频 | 128x128；SpiLcd | 电池/电源管理；LED/灯效 |
| 80 | `minsi-k08-dual` | esp32s3 | minsi-k08-dual | 带屏显示、触摸交互、蜂窝联网 | 双网络 + ML307/4G + WiFi | 无外置 codec/I2S 简化音频 | 240x240；SpiLcd | 触摸；电池/电源管理；LED/灯效 |
| 81 | `mixgo-nova` | esp32s3 | mixgo-nova | 带屏显示、WiFi 联网 | WiFi | ES8374 音频 | 128x160；SpiLcd | LED/灯效 |
| 82 | `movecall-cuican-esp32s3` | esp32s3 | movecall-cuican-esp32s3 | 带屏显示、WiFi 联网 | WiFi | ES8311 音频 | 240x240；SpiLcd | LED/灯效 |
| 83 | `movecall-moji-esp32s3` | esp32s3 | movecall-moji-esp32s3 | 带屏显示、WiFi 联网 | WiFi | ES8311 音频 | 240x240；SpiLcd | LED/灯效 |
| 84 | `nulllab-ai-vox-v3` | esp32s3 | nulllab-ai-vox-v3 | 带屏显示、蜂窝联网 | 双网络 + ML307/4G + WiFi | 参考声道/AEC | 240x240；SpiLcd | 电池/电源管理；LED/灯效 |
| 85 | `otto-robot` | esp32s3 | otto-robot | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网、运动控制 | WiFi | 无外置 codec/I2S 简化音频 | 240x240；SpiLcd | 摄像头；触摸；电池/电源管理；舵机/运动控制；LED/灯效 |
| 86 | `sensecap-watcher` | esp32s3 | sensecap-watcher | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网、旋钮/编码器 | WiFi | 参考声道/AEC | 412x412；SpiLcd | 摄像头；触摸；电池/电源管理；旋钮/编码器；LED/灯效 |
| 87 | `sp-esp32-s3-1.28-box` | esp32s3 | sp-esp32-s3-1.28-box | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频 | 240x240；SpiLcd | 触摸；电池/电源管理；LED/灯效 |
| 88 | `sp-esp32-s3-1.54-muma` | esp32s3 | sp-esp32-s3-1.54-muma | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频 | 240x240；SpiLcd | 触摸；电池/电源管理；LED/灯效 |
| 89 | `taiji-pi-s3` | esp32s3 | taiji-pi-s3, taiji-pi-s3-pdm | 带屏显示、触摸交互、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 360x360；SpiLcd | 触摸；LED/灯效 |
| 90 | `tudouzi` | esp32s3 | tudouzi | 蜂窝联网 | ML307/4G | ES8311+ES7210/Box 音频链路；参考声道/AEC | 128x64；Oled；NoDisplay | 电池/电源管理；LED/灯效 |
| 91 | `waveshare/esp32-s3-audio-board` | esp32s3 | esp32-s3-audio-board | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 320x172；SpiLcd | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 92 | `waveshare/esp32-s3-cam` | esp32s3 | esp32-s3-cam-2, esp32-s3-cam-2.8, esp32-s3-cam-3.5, esp32-s3-cam-1.83 | 视觉/摄像头、带屏显示、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 240x320；SpiLcd | 摄像头；LED/灯效 |
| 93 | `waveshare/esp32-s3-epaper-1.54` | esp32s3 | esp32-s3-epaper-1.54-v2, esp32-s3-epaper-1.54-v1 | 带屏显示、WiFi 联网 | WiFi | ES8311 音频 | EPaper | 电池/电源管理；LED/灯效 |
| 94 | `waveshare/esp32-s3-epaper-3.97` | esp32s3 | esp32-s3-epaper-3.97 | 带屏显示、WiFi 联网 | WiFi | ES8311 音频 | EPaper | 电池/电源管理 |
| 95 | `waveshare/esp32-s3-lcd-0.85` | esp32s3 | esp32-s3-lcd-0.85 | 带屏显示、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 128x128；SpiLcd | 电池/电源管理；LED/灯效 |
| 96 | `waveshare/esp32-s3-rlcd-4.2` | esp32s3 | esp32-s3-rlcd-4.2 | 触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 无/未明确识别 | 触摸；电池/电源管理 |
| 97 | `waveshare/esp32-s3-touch-amoled-1.32` | esp32s3 | esp32-s3-touch-amoled-1.32 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频 | SpiLcd；Amoled | 触摸；电池/电源管理；LED/灯效 |
| 98 | `waveshare/esp32-s3-touch-amoled-1.43c` | esp32s3 | esp32-s3-touch-amoled-1.43c | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | SpiLcd；Amoled | 触摸；LED/灯效 |
| 99 | `waveshare/esp32-s3-touch-amoled-1.75` | esp32s3 | esp32-s3-touch-amoled-1.75, esp32-s3-touch-amoled-1.75c | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 466x466；SpiLcd；Amoled | 触摸；电池/电源管理；LED/灯效 |
| 100 | `waveshare/esp32-s3-touch-amoled-1.8` | esp32s3 | esp32-s3-touch-amoled-1.8 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频 | 368x448；SpiLcd；Amoled | 触摸；电池/电源管理；LED/灯效 |
| 101 | `waveshare/esp32-s3-touch-amoled-2.06` | esp32s3 | esp32-s3-touch-amoled-2.06 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 410x502；SpiLcd；Amoled | 触摸；电池/电源管理；LED/灯效 |
| 102 | `waveshare/esp32-s3-touch-lcd-1.46` | esp32s3 | esp32-s3-touch-lcd-1.46 | 带屏显示、触摸交互、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 412x412；SpiLcd | 触摸；电池/电源管理 |
| 103 | `waveshare/esp32-s3-touch-lcd-1.54` | esp32s3 | esp32-s3-touch-lcd-1.54 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 240x240；SpiLcd | 触摸；电池/电源管理；LED/灯效 |
| 104 | `waveshare/esp32-s3-touch-lcd-1.83` | esp32s3 | esp32-s3-touch-lcd-1.83 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 240x284；SpiLcd | 触摸；电池/电源管理 |
| 105 | `waveshare/esp32-s3-touch-lcd-1.85` | esp32s3 | esp32-s3-touch-lcd-1.85 | 带屏显示、触摸交互、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 360x360；SpiLcd | 触摸；电池/电源管理 |
| 106 | `waveshare/esp32-s3-touch-lcd-1.85c` | esp32s3 | esp32-s3-touch-lcd-1.85c | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；无外置 codec/I2S 简化音频；参考声道/AEC | 360x360；SpiLcd | 触摸 |
| 107 | `waveshare/esp32-s3-touch-lcd-3.49` | esp32s3 | esp32-s3-touch-lcd-3.49 | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 172x640 | 触摸 |
| 108 | `waveshare/esp32-s3-touch-lcd-3.5` | esp32s3 | esp32-s3-touch-lcd-3.5 | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频 | 480x320；SpiLcd | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 109 | `waveshare/esp32-s3-touch-lcd-3.5b` | esp32s3 | esp32-s3-touch-lcd-3.5b | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频 | 480x320 | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 110 | `waveshare/esp32-s3-touch-lcd-4.3c` | esp32s3 | esp32-s3-touch-lcd-4.3c | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | RgbLcd | 触摸；电池/电源管理 |
| 111 | `waveshare/esp32-s3-touch-lcd-4b` | esp32s3 | esp32-s3-touch-lcd-4b | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；参考声道/AEC | 480x480；RgbLcd | 触摸；电池/电源管理 |
| 112 | `xingzhi-abs-2.0` | esp32s3 | xingzhi-abs-2.0 | 带屏显示、触摸交互、蜂窝联网、运动控制 | 双网络 + ML307/4G + WiFi | ES8311 音频；参考声道/AEC | 240x240；SpiLcd | 触摸；电池/电源管理；舵机/运动控制 |
| 113 | `xingzhi-cube-0.85tft-ml307` | esp32s3 | xingzhi-cube-0.85tft-ml307 | 带屏显示、蜂窝联网 | ML307/4G + WiFi | 无外置 codec/I2S 简化音频 | 128x128；SpiLcd | 电池/电源管理 |
| 114 | `xingzhi-cube-0.85tft-wifi` | esp32s3 | xingzhi-cube-0.85tft-wifi | 带屏显示、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 128x128；SpiLcd | 电池/电源管理 |
| 115 | `xingzhi-cube-0.96oled-ml307` | esp32s3 | xingzhi-cube-0.96oled-ml307 | 蜂窝联网 | 双网络 + ML307/4G + WiFi | 无外置 codec/I2S 简化音频 | 128x64；Oled；NoDisplay | 电池/电源管理；LED/灯效 |
| 116 | `xingzhi-cube-0.96oled-wifi` | esp32s3 | xingzhi-cube-0.96oled-wifi | WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 128x64；Oled；NoDisplay | 电池/电源管理；LED/灯效 |
| 117 | `xingzhi-cube-1.54tft-ml307` | esp32s3 | xingzhi-cube-1.54tft-ml307, xingzhi-cube-1.54tft-ml307-wechatui | 带屏显示、蜂窝联网 | 双网络 + ML307/4G + WiFi | 无外置 codec/I2S 简化音频 | 240x240；SpiLcd | 电池/电源管理 |
| 118 | `xingzhi-cube-1.54tft-wifi` | esp32s3 | xingzhi-cube-1.54tft-wifi | 带屏显示、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 240x240；SpiLcd | 电池/电源管理 |
| 119 | `xingzhi-metal-1.54-wifi` | esp32s3 | xingzhi-metal-1.54-wifi | 带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311 音频；参考声道/AEC | 240x240；SpiLcd | 触摸；电池/电源管理 |
| 120 | `yunliao-s3` | esp32s3 | yunliao-s3 | 带屏显示、触摸交互、蜂窝联网 | 双网络 + ML307/4G + WiFi | ES8388 音频；参考声道/AEC | 320x240；SpiLcd | 触摸；电池/电源管理 |
| 121 | `zhengchen-1.54tft-ml307` | esp32s3 | zhengchen-1.54tft-ml307 | 带屏显示、蜂窝联网 | 双网络 + ML307/4G + WiFi | 无外置 codec/I2S 简化音频 | 240x240 | 电池/电源管理 |
| 122 | `zhengchen-1.54tft-wifi` | esp32s3 | zhengchen-1.54tft-wifi | 带屏显示、WiFi 联网 | WiFi | 无外置 codec/I2S 简化音频 | 240x240；SpiLcd | 电池/电源管理 |
| 123 | `zhengchen-cam` | esp32s3 | zhengchen-cam | 视觉/摄像头、带屏显示、触摸交互、WiFi 联网 | WiFi | ES8311+ES7210/Box 音频链路；自定义音频；参考声道/AEC | 320x240；SpiLcd | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 124 | `zhengchen-cam-ml307` | esp32s3 | zhengchen-cam-ml307 | 视觉/摄像头、带屏显示、触摸交互、蜂窝联网 | 双网络 + ML307/4G + WiFi | ES8311+ES7210/Box 音频链路；自定义音频；参考声道/AEC | 320x240；SpiLcd | 摄像头；触摸；电池/电源管理；LED/灯效 |
| 125 | `zhengchen-minicam` | esp32s3 | zhengchen-minicam | 视觉/摄像头、触摸交互、WiFi 联网 | WiFi | ES8388 音频；参考声道/AEC | 240x320；SpiLcd；NoDisplay | 摄像头；触摸；电池/电源管理；LED/灯效 |

## 如何读这份表

- `芯片` 对应 ESP-IDF 的 target，构建前需要与 `idf.py set-target` 一致。
- `构建名` 来自 `config.json` 的 `builds.name`，有些目录下面有多个构建变体，例如不同屏幕尺寸、UI 风格或硬件版本。
- `联网` 里的 ML307/NT26 表示蜂窝通信模块相关板级适配；很多双网络板会同时出现 WiFi 和 4G。
- `音频` 里的参考声道/AEC 通常表示板级代码启用了回采参考声道或设备侧回声消除路径。
- `显示` 里的 SpiLcd/RgbLcd/MipiLcd/Oled/AMOLED/EPaper 是从显示驱动类型和源码关键字归类的。
