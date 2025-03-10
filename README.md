# CH32V003 RISC-V Mini Game Console
Mini Game Console utilizing the CH32V003J4M6 ultra-cheap (10 cents by the time of writing) 32-bit RISC-V microcontroller, an SSD1306 128x64 pixels OLED display and CR/LIR2032 coin cell battery holder.

- Project Video (YouTube): https://youtu.be/1W7Z0BodhWk
- PCB Design Files (EasyEDA): https://oshwlab.com/wagiminator/ch32v003j4m6-game-console

![GameConsole_pic1.jpg](https://raw.githubusercontent.com/wagiminator/CH32V003-GameConsole/main/documentation/GameConsole_pic1.jpg)

# Hardware
## Schematic
![GameConsole_wiring.png](https://raw.githubusercontent.com/wagiminator/CH32V003-GameConsole/main/documentation/GameConsole_wiring.png)

## The CH32V003 Family of 32-bit RISC-V Microcontrollers
The CH32V003 series is a collection of industrial-grade general-purpose microcontrollers that utilize the QingKe RISC-V2A core design supporting the RV32EC instruction set. These microcontrollers are equipped with various features such as a 48MHz system main frequency, wide voltage support, a single-wire serial debug interface, low power consumption, and an ultra-small package. Additionally, the CH32V003 series includes a built-in set of components including a DMA controller, a 10-bit ADC, op-amp comparators, multiple timers, and standard communication interfaces such as USART, I2C, and SPI.

# Games
## Tiny Invaders
Tiny Invaders was originally developed by [Daniel Champagne](https://www.tinyjoypad.com/) for the ATtiny85. It is an adaptation of the classic game Space Invaders. The player controls a laser cannon that moves horizontally along the bottom of the screen. The objective is to defend the Earth from waves of descending alien invaders. The aliens move side to side, gradually descending towards the player, and the player's goal is to destroy them before they reach the bottom of the screen.

The player can shoot projectiles at the aliens and must strategically time their shots to hit the moving targets. As the game progresses, the aliens' movement becomes faster, making it more challenging to eliminate them. Additionally, the aliens periodically fire back at the player, creating a sense of urgency and adding to the gameplay difficulty.

![GameConsole_invaders_1.png](https://raw.githubusercontent.com/wagiminator/CH32V003-GameConsole/main/documentation/GameConsole_invaders_1.png)
![GameConsole_invaders_2.png](https://raw.githubusercontent.com/wagiminator/CH32V003-GameConsole/main/documentation/GameConsole_invaders_2.png)

## Tiny Lander
Tiny Lander was originally developed by [tscha70](https://github.com/tscha70/TinyLanderV1.0) for the ATtiny85. It is an adaptation of the classic game Lunar Lander that simulates the experience of piloting a spacecraft and landing it safely on the moon's surface. The objective of the game is to control the descent of the lunar lander module, adjusting the thrust and direction to ensure a smooth landing without crashing or running out of fuel. It requires careful maneuvering and precision to navigate the gravitational forces and terrain obstacles present on the moon.

![GameConsole_lander_1.png](https://raw.githubusercontent.com/wagiminator/CH32V003-GameConsole/main/documentation/GameConsole_lander_1.png)
![GameConsole_lander_2.png](https://raw.githubusercontent.com/wagiminator/CH32V003-GameConsole/main/documentation/GameConsole_lander_2.png)

If you hold down the UP button on the start screen while pressing the fire button, the game will automatically start in a later level. On the other hand, if you hold down the DOWN button, you get 255 lives.

## Tiny Tris
Tiny Tris was originally developed by [Daniel Champagne](https://www.tinyjoypad.com/) for the ATtiny85. It is an adaptation of the well-known game Tetris. The objective of Tetris is to manipulate and arrange the falling Tetriminos to create complete horizontal lines without any gaps. When a line is completed, it clears from the playfield, and the player earns points. As the game progresses, the Tetriminos fall faster, increasing the challenge. If the Tetriminos stack up and reach the top of the playfield, the game ends.

![GameConsole_tris_1.png](https://raw.githubusercontent.com/wagiminator/CH32V003-GameConsole/main/documentation/GameConsole_tris_1.png)
![GameConsole_tris_2.png](https://raw.githubusercontent.com/wagiminator/CH32V003-GameConsole/main/documentation/GameConsole_tris_2.png)

## Tiny Arkanoid
Tiny Arkanoid was originally developed by [Daniel Champagne](https://www.tinyjoypad.com/) for the ATtiny85. It is an adaptation of the classic game Arkanoid. The player controls a paddle at the bottom of the screen and uses it to bounce a ball against a wall of bricks at the top.

The objective of the game is to destroy all the bricks by hitting them with the ball. Each brick that is hit will disappear, and the player earns points for each brick destroyed. The ball bounces off the walls and the paddle, and the player must maneuver the paddle to keep the ball in play and prevent it from falling off the bottom of the screen.

![GameConsole_arkanoid_1.png](https://raw.githubusercontent.com/wagiminator/CH32V003-GameConsole/main/documentation/GameConsole_arkanoid_1.png)
![GameConsole_arkanoid_2.png](https://raw.githubusercontent.com/wagiminator/CH32V003-GameConsole/main/documentation/GameConsole_arkanoid_2.png)

## Tiny Pacman
Tiny Pacman was originally developed by [Daniel Champagne](https://www.tinyjoypad.com/) for the ATtiny85. The player controls a round character called Pacman, who must navigate through a maze filled with pellets and various types of enemies, known as ghosts. The objective of the game is for Pacman to eat all the pellets in the maze while avoiding the ghosts.

![GameConsole_pacman_1.png](https://raw.githubusercontent.com/wagiminator/CH32V003-GameConsole/main/documentation/GameConsole_pacman_1.png)
![GameConsole_pacman_3.png](https://raw.githubusercontent.com/wagiminator/CH32V003-GameConsole/main/documentation/GameConsole_pacman_3.png)

# Compiling and Uploading Firmware
## Programming and Debugging Devices
To program the CH32V003 microcontroller, you will need a special programming device which utilizes the proprietary single-wire serial debug interface (SDI). The [WCH-LinkE](http://www.wch-ic.com/products/WCH-Link.html) (pay attention to the "E" in the name) is a suitable device for this purpose and can be purchased commercially for around $3. This debugging tool is not only compatible with the CH32V003 but also with other WCH RISC-V and ARM-based microcontrollers.

![CH32V003_wch-linke.jpg](https://raw.githubusercontent.com/wagiminator/Development-Boards/main/CH32V003F4P6_DevBoard/documentation/CH32V003_wch-linke.jpg)

As part of his [ch32v003fun](https://github.com/cnlohr/ch32v003fun) project, Charles Lohr has also developed open-source programmers/debuggers based on STM32F042 and ESP32S2. Furthermore, the schematic diagram of the WCH-LinkE based on the CH32V305F is available on the manufacturer's [website](https://www.wch.cn/products/WCH-Link.html), but the [firmware](https://github.com/openwch/ch32v003) can only be downloaded as a binary file.

To upload the firmware, you need to ensure that the Game Console is switched off or the battery is removed. Then, you should make the following connections to the WCH-LinkE:

```
WCH-LinkE     GameConsole
+-------+      +-------+
|  SWDIO| <--> |DIO    |
|    3V3| ---> |3V3    |
|    GND| ---> |GND    |
+-------+      +-------+
```

If the blue LED on the WCH-LinkE stays on after plugging it into the USB port, then the device is in ARM mode and needs to be switched to RISC-V mode first. This can be done by selecting "WCH-LinkRV" using the software provided by WCH (MounRiver Studio or WCH-LinkUtility). Alternatively, the ModeS button on the device can be held down while plugging it into the USB port. More information can be found in the [WCH-Link User Manual](http://www.wch-ic.com/downloads/WCH-LinkUserManual_PDF.html).

## Compiling and Uploading (Linux)
To use the WCH-LinkE on Linux, you need to grant access permissions beforehand by executing the following commands:
```
echo 'SUBSYSTEM=="usb", ATTR{idVendor}=="1a86", ATTR{idProduct}=="8010", MODE="666"' | sudo tee /etc/udev/rules.d/99-WCH-LinkE.rules
echo 'SUBSYSTEM=="usb", ATTR{idVendor}=="1a86", ATTR{idProduct}=="8012", MODE="666"' | sudo tee -a /etc/udev/rules.d/99-WCH-LinkE.rules
sudo udevadm control --reload-rules
```

Install the GCC compiler, if you want to compile the firmware yourself:
```
sudo apt install build-essential libnewlib-dev gcc-riscv64-unknown-elf libusb-1.0-0-dev libudev-dev
```

Switch off the Game Console or remove the battery. Connect the Console via the 3-pin header to the programming device. Open a terminal and navigate to the folder with the makefile. Run the following command to compile and upload:
```
make flash
```

If you want to just upload the pre-compiled binary, run the following command instead:
```
./tools/minichlink -w <firmware>.bin flash -b
```

## Uploading Firmware Binary (Windows/Mac)
WCH offers the free but closed-source software [WCH-LinkUtility](https://www.wch.cn/downloads/WCH-LinkUtility_ZIP.html) to upload the precompiled binary with Windows. Select the "WCH-LinkRV" mode in the software, open the <firmware>.bin file and upload it to the microcontroller.

Alternatively, there is a platform-independent open-source tool called minichlink developed by Charles Lohr (CNLohr), which can be found [here](https://github.com/cnlohr/ch32v003fun/tree/master/minichlink). It can be used with Windows, Linux and Mac.

# References, Links and Notes
- [EasyEDA Design Files](https://oshwlab.com/wagiminator)
- [DanielC: Tinyjoypad](https://www.tinyjoypad.com/)
- [CNLohr: ch32003fun](https://github.com/cnlohr/ch32v003fun)
- [WCH: CH32V003 datasheets](http://www.wch-ic.com/products/CH32V003.html)
- [WCH: WCH-Link user manual](http://www.wch-ic.com/downloads/WCH-LinkUserManual_PDF.html)
- [WCH: Official Store on AliExpress](https://wchofficialstore.aliexpress.com)

![GameConsole_pic2.jpg](https://raw.githubusercontent.com/wagiminator/CH32V003-GameConsole/main/documentation/GameConsole_pic2.jpg)

# License

![license.png](https://i.creativecommons.org/l/by-sa/3.0/88x31.png)

This work is licensed under Creative Commons Attribution-ShareAlike 3.0 Unported License. 
(http://creativecommons.org/licenses/by-sa/3.0/)
