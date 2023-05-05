# Frames
A clone of the Mutable Instruments Frames module with the use of the STM32F103 Blue Pill board.

<img height="800" src="https://user-images.githubusercontent.com/97026614/236367816-3db1058e-74cc-4f85-8c20-534c7b78713d.jpg">

<img height="500" src="https://user-images.githubusercontent.com/97026614/236368017-267b4801-315e-4123-8ec2-91901bd83b07.jpeg"> <img height="500" src="https://user-images.githubusercontent.com/97026614/236368081-db558a06-ff9b-4231-ac65-a199a927d07e.jpeg"> 

<img height="500" src="https://user-images.githubusercontent.com/97026614/236368170-12cc0d32-6658-45f0-be28-00a64f01d27a.jpeg"> <img height="500" src="https://user-images.githubusercontent.com/97026614/236368258-676627c9-2f30-4853-9ebe-af4f76e9a7a6.jpeg">

## Module Build and PCBs
If you want to build the module yourself, I uploaded firmware, schematic, BOM and Gerber files for the PCB.

There are two different versions for the control board, an "original" and a "Thonk" version.
Reason is that for my own module, I am using specific potentiometers - 16K4 series from Supertech Electronics - and 3.5mm jack sockets - MJ-355 from Marushin - available at my local electronics shop.

<img width="300" alt="OrigCtrlPCBFront" src="https://user-images.githubusercontent.com/97026614/230913339-03c6ba1d-3a83-4cbc-a96a-c415498f99b9.png">

However, since most DIY projects for Eurorack modules out there are using potentiometers from ALPHA and so-called THONKICONN jacks, as they are provided by Thonk in the UK, I also created a version with footprints for those components.
Choose the one you need.

<img width="300" alt="CtrlPCBThonk" src="https://user-images.githubusercontent.com/97026614/230913456-7f74d3d0-3f92-4ab7-9388-9e2fb55da0b8.png">

The layout of the main PCB is slightly different for both versions, as I needed to relocate the board connection points due to the size difference of the jacks in both versions. Make sure to use the correct pair of Gerber files.

<img width="300" alt="MainPCB" src="https://user-images.githubusercontent.com/97026614/230913521-842da377-7302-4a35-ab89-c16e38aaa3ca.png">

I created the Gerber files with the online tool EasyEDA and ordered it at JLCPCB.
I cannot guarantee, if this set of zipped Gerber files works also for other providers, like e.g. PCBWay. I have not tried that. But I saw online, that others did it.

## Panel Layout
I added the information about hole coordinates for the front panel in the folder PanelLayout, referring to the component layout in the Gerber files.

## Additional Information about specific Components
Most of the components are through-hole, including the microchip part, thanks to the available Blue Pill board. There are a few SMD components, which I listed here.
- DAC8552 (DAC, 8-VSSOP package, the most challenging component due to its size)
- LM1117-3.3 (voltage regulator, SOT-223 package)
- LM4040B25 and LM4040B10 (voltage regulators, SOT-23-3 package)
- MMBT3904 (SMD version of the 2N3904 transistor, SOT-23-3 Package)
- 0.1uF bypass caps for ICs (1608 package)

Concerning the resistor size, I am usually using small-size resistors, about half the length of the usual size, so they need less space on the PCB. If you want to use my Gerber files, you have to consider tht fact. You might still use normal size resistors and put them in a standing position on the boards. Should also work fine.

## Firmware
I shared the .hex files for the STM32F103 chip (bootloader and main) in the folder Firmware.

The upload process is the same, as for my Braids clone. You can check out my [Braids video](https://youtu.be/TBMySGm7jKk) about how to program the Blue Pill board.

Alternative firmware versions available, like e.g. Sheep or the Parasite version, both available as .wav files can also be uploaded via the procedure described in the official Mutable Instruments manual.

Check [this YouTube video](https://youtu.be/xhDt-fGgXi8) for more details about the firmware update process.

## STM32F103 Version
CAUTION! There are three different versions of the Blue Pill board available.
The difference is the version of the ST32F103 microchip on the board.
The versions differ in the flash memory size:
- STM32F103C6T6: 32kB flash memory
- STM32F103C8T6: 64kB flash memory
- STM32F103CBT6: 128kB flash memory

The code size requires the 128kB version.
However, that version might be difficult to find, if available at all.
But it turned out, that STM3F103C8T6 is also ok for this module.

## Calibration
The calibration procedure is the same, as the one for the original module from Mutable Instruments.

### CV input calibration
This automatic procedure calibrates the V/Oct input (scale and offset), the FM input (offset), and the level input (offset).
1. Set the FREQUENCY knob to its center position.
2. Connect a patch cable to the FM input. Leave the other end of the cable unplugged (this prevents the normalling to \~1 semitone to be activated).
3. Connect a patch cable to the Level input. Leave the other end of the cable unplugged (this prevents the normalling to full scale to be activated).
4. Connect a MIDI>CV interface or precision voltage source to the V/Oct input.
5. Hold the Mode switch for one second. All LEDs are lit (in yellow in the original version).
6. Play a C2 note, or send a 1V voltage from your CV source.
7. Press the Mode switch. The color of all LEDs are changing (to green in the original version).
8. Play a C4 note, or send a 3V voltage from your CV source.
9. Press the Mode switch.

### Bipolar output offset calibration
1. Remove any patch cable from the trigger input.
2. Set the mode to AD or AR (mode LED is on, any color).
3. Set the range to medium (range LED is off).
4. Measure the voltage on the bipolar output. 
5. Adjust the trimmer on the back of the board so that this voltage reaches 0V.
