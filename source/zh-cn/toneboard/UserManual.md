title: Khadas Tone Board 用户手册
---

感谢选购Khadas Tone Board，现在开始享受高品质音乐吧～
![Tone Board Overview](/images/toneboard/ToneboardOverview.jpg)



## 包装和配件
VIMs 版本|通用版本|
---|:---
Tone Board (已焊接20脚排针和40脚排座)|Tone Board
USB Type C数据线|USB Type C数据线
螺丝|螺丝
-|40脚排座
-|20脚排针

![Tone Board Recipes](/images/toneboard/ToneboardRecipes.jpg)


## 设备连接

* ### VIMs版本

步骤|操作|
---|:---
1| 把Tone Board和VIMs通过40脚排座连接起来
2| 连接音频线到RCA座子
3| 连接HDMI线到显示器
4| 连接5V电源

![Tone Board Connection VIMs](/images/toneboard/ToneboardConnectionVIMs.png)


* ### 通用版本

步骤|操作|
---|:---
1| 连接音频线到RCA座子
2| 通过USB Type C数据线连接Tone Board和PC

![Tone Board Connection General](/images/toneboard/ToneboardConnectionGeneral.jpg)


## 设置
大多数平台已经集成了Tone Board驱动，但是Windows平台需要额外安装驱动。
* ### VIMs
  确保VIM1固件版本为`VIM_Nougat_V180524`或更新。
  确保VIM2固件版本为`VIM2_Nougat_V180413`或更新。

* ### Windows
  以Windows 10为例进行说明，Windows 7和Windows XP也是类似的。
  *  安装XMOS驱动
     * [下载](http://www.mediafire.com/file/hpjivuk0dbi8jqt/Thesycon-Stereo-USB-Audio-Driver-v224.rar)驱动
     * 解压并运行`setup.exe`来安装驱动
     * 安装完成后可以在设备管理器看到XMOS设备
![Tone Board Windows Setup1](/images/toneboard/ToneboardWindowsSetup1.png)
  *  选择声卡为Tone Board
     * 点击底部任务栏的声音图标
![Tone Board Windows Setup2](/images/toneboard/ToneboardWindowsSetup2.jpg)
     * 选择XMOS XS1-U8 DJ为默认输出声卡
![Tone Board Windows Setup3](/images/toneboard/ToneboardWindowsSetup3.jpg)

* ### Ubuntu
  *  选择声卡为Tone Board
![Tone Board Ubuntu Setup](/images/toneboard/ToneboardUbuntuSetup.jpg)

* ### MacOS
  *  选择声卡为Tone Board
![Tone Board Mac OS Setup](/images/toneboard/ToneboardMacosSetup.jpg)

* ### 树莓派
  *  选择声卡为Tone Board

     * Volumio
![Tone Board Rpi Setup](/images/toneboard/ToneboardRpiSetup.jpg)

     * Raspbian
```
1.list sound card
$ aplay -l

2.switch sound card
$vi ~/.asoundrc

3.replace card 0 for XMOS sound card
pcm.!default {
    type hw
    card 0
}

ctl.!default {
    type hw
    card 0
}
```

## 接口描述
No|Ports|Function|
---|:---|:---
1|USB-C    |Power supply & data transmission
2|S/PDIF   |S/PDIF input/output
3|L             |Audio left channel output
4|R            |Audio right channel output
5|20Pin Header  |Debug Port, update XMOS firmware
6|40Pin Header  |VIMs connector (Power supply & data transmission)
7|I2S         |VIMs I2S output
8|8 Channel Ext |XMOS 8 Channel extend
9|OLED     |VIMs OLED display
10|Power LED     |Power supply indicator

![Tone Board Ports](/images/toneboard/ToneboardPorts.png)

**No5**: 20 Pin Header Pinout (J4)

SIGNAL| PIN|PIN|SIGNAL
---|:---|:---|:---
VCC_3V3|1|11|TONE_5V
Linux_TX|2|12|TONE_5V
Linux_RX|3|13|GND
GND|4|14|GND
XL_DN1|5|15|XMOS_RST
XL_DN0|6|16|XMOS_TDO
XL_UP0|7|17|XMOS_TDI
XL_UP1|8|18|XMOS_TCK
XMOS_3V3|9|19|XMOS_TMS
GND|10|20|GND

**No6:** 40 Pin Header Pinout (J1)

SIGNAL| PIN|PIN|SIGNAL
---|:---|:---|:---
5V_1|1|21|GND5
5V_2|2|22|OLED_SCL
VIM_DN|3|23|OLED_SDA
VIM_DP|4|24|GND6
GND|5|25|-
-|6|26|-
-|7|27|VCC_3V3
-|8|28|GND7
GND|9|29|I2S_SCLK
ADC0|10|30|I2S_MCLK
-|11|31|I2S_SDO
-|12|32|I2S_LRCK
VIM_SPDIF|13|33|I2S_SDI
GND3|14|34|GND8
UART_RX_AO_B/SPDIF_MODE|15|35|OLED_PWREN
UART_TX_AO_B/SPDIF_IN_MODE|16|36|-
GND4|17|37|OLED_RST
Linux_RX|18|38|-
Linux_TX|19|39|MUTE
VCC_3V3|20|40|GND9

**No7:** I2S FPC Connectors Pinout (J9)

PIN|SIGNAL
---|:---
1|TONE_5V
2|GND
3|VCC_3V3
4|GND
5|I2S_SCLK
6|I2S_MCLK
7|I2S_SDI
8|I2S_LRCK
9|I2S_SDO
10|GND

**No8:** 8 Channel Ext  FPC Connectors Pinout (J3)

PIN|SIGNAL
---|:---
1-3|TONE_5V
4-6|GND
7,8|XMOS_3V3
9|XMOSIO3
10|XMOSIO2
11|XMOSIO1
12|ADC0
13|VOLUME
14|XMOS_SCL
15|XMOS_SDA
16|MUTE
17|DAC_RST
18|GND
19|MCLK
20|GND
21|LRCK/DSD_CLK
22|GND
23|BCLK/DSD_1
24|GND
25|SIN0/DSD_2
26|SIN1/DSD_3
27|SIN2/DSD_4
28|SIN3/DSD_5
29|DSD_6
30|GND

**No9:** OLED  FPC Connectors Pinout (J8)

PIN|SIGNAL
---|:---
1|TONE_5V
2|TONE_5V
3|OLED_SCL
4|OLED_SDA
5|GND
6|-
7|OLED_RST
8|OLED_PWREN
9|-
10|GND


## FAQs
* 如何扩展8通道输出？
XMOS支持8通道模拟输出，Tone Board DAC（ES9038Q2M）已经用了2通道。用户可以增加DAC 8通道扩展。

