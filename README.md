ESP32 Devkit Type C
===================

## 2022 Update ([*@moucha19*](https://github.com/moucha19))

First of all, I would like to thank the original author for his work. I wanted to make this DevKit as soon as I saw it. However, there were some issues that I thought needed fixing. For example, some components were unavailable or not up-to-date. Here is a full list of my updates that all together make revision **EB**:

* CH340G was changed to CH340C to remove the need for external crystal. I also noticed that it's powered from VBUS, which according to datasheet means that the data lines will run on 5 volts. This might not kill ESP32 right away, but from what I read, it isn't good.
* I replaced MP2359 with MP2259, because the former is not recommended for new designs. JLCPCB still has MP2359s, but I wanted this update to last a while.
* USB-C connector was changed to TYPE-C-31-M-12, which I already had home. Push buttons were also changed for the same reason, but in my opinion they look good and are also pretty common.
* Inductor was replaced with currently available part 
* Some components were moved around to avoid unnecesary DRC errors
* I made pads around ESP32 larger for easier manual soldering, since I don't intend to use SMT assembly service. However, I still generated files for those who do. Use [SMT BOM](jlcpcb/bom_jlc_smt.csv) in the order to get only recommended parts (no USB-C, buttons or headers).
* Project was upgraded to Kicad 6.0

# Description

This PCB is a USB Type C enabled ESP32 development board. It is pin-compatible
with the ESP32 Devkit C but sports a slightly decreased width to fit on a
standard breadboard.  

# Features

* USB Type C
* pin-compatible with ESP32 Devkit
* fits on standard breadboard
* onboard antenna
* jumper to short USB protection diode

Furthermore this board is optimized for JLCPCB assembly, a Chinese SMT PCB
assembly service. All components on this board, except the USB Type C connector,
the push buttons and the pin headers can be assembled by them for around ~$8
including PCB manufacturing and components.

![Devkit](/resources/revEB.png)

# Assembly

There is an
[interactive HTML BOM](https://htmlpreview.github.io/?https://github.com/moucha19/ESP32-Devkit-Type-C/blob/master/docs/ibom.html)
to help you assemble the board.

Assuming you are using JLCPCB SMT assembly you will need to populate just the
following parts by hand:

| Reference  | Description            | LCSC                                                                                                                  |
|------------|------------------------|-----------------------------------------------------------------------------------------------------------------------|
| J1         | USB Type C connector   | [C165948](https://www.lcsc.com/product-detail/USB-Type-C_Korean-Hroparts-Elec-TYPE-C-31-M-12_C165948.html)    |
| SW1, SW2   | RESET/BOOT push button | [C589212](https://lcsc.com/product-detail/Tactile-Switches_RI-SHENG-ST-1188_C589212.html)    |
| J2, J3     | Pin headers            | [C2337](https://lcsc.com/product-detail/Pin-Header-Female-Header_BOOMELE-Boom-Precision-Elec-2-54mm-1x40P_C2337.html) |
