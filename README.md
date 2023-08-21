# Frames - 4-Channel Keyframer/Mixer Eurorack Module
A clone of the Mutable Instruments Frames module with the use of the STM32F103 Blue Pill board.

<img height="800" src="https://user-images.githubusercontent.com/97026614/236367816-3db1058e-74cc-4f85-8c20-534c7b78713d.jpg">

<img height="500" src="https://user-images.githubusercontent.com/97026614/236368017-267b4801-315e-4123-8ec2-91901bd83b07.jpeg"> <img height="500" src="https://user-images.githubusercontent.com/97026614/236368081-db558a06-ff9b-4231-ac65-a199a927d07e.jpeg"> 

<img height="500" src="https://user-images.githubusercontent.com/97026614/236368170-12cc0d32-6658-45f0-be28-00a64f01d27a.jpeg"> <img height="500" src="https://user-images.githubusercontent.com/97026614/236368258-676627c9-2f30-4853-9ebe-af4f76e9a7a6.jpeg">

## Module Build and PCBs
If you want to build the module yourself, I uploaded firmware, schematic, BOM and Gerber files for the PCB.

There are two different versions for the control board, an "original" and a "Thonk" version.
Reason is that for my own module, I am using specific potentiometers - 16K4 series from Supertech Electronics - and 3.5mm jack sockets - MJ-355 from Marushin - available at my local electronics shop.

<img width="300" alt="Frames_CtrlPCB_Orig" src="https://user-images.githubusercontent.com/97026614/236384841-ecda3ace-aa2b-498c-9491-87a92e6ad552.png">

However, since most DIY projects for Eurorack modules out there are using potentiometers from ALPHA and so-called THONKICONN jacks, as they are provided by Thonk in the UK, I also created a version with footprints for those components.
Choose the one you need.

<img width="300" alt="Frames_CtrlPCB_Thonk" src="https://user-images.githubusercontent.com/97026614/236384960-e02f76fd-f46f-4d09-a1d5-d10e453249d3.png">

The layout of the main PCB is the same for both versions.

<img width="300" alt="Frames_MainPCB" src="https://user-images.githubusercontent.com/97026614/236385007-8943d4b2-a96c-4268-aac2-eb99cd04bfe4.png">

I created the Gerber files with the online tool EasyEDA and ordered it at JLCPCB.

## Panel Layout
I added the information about hole coordinates for the front panel in the folder PanelLayout, referring to the component layout in the PCB Gerber files.

In addition, there is another Gerber file for the panel, following the HP standard. My own modules do not follow that width standard, as I am only using sliding nuts in my racks.

You can use the panel Gerber file to have the panel built out of PCB material.

## Central Knob Illumination
The original Mutable Instruments design uses a transparent central knob with one RGB LED behind it to create the different colors for each frame. I added another RGB LED in order to get a more evenly spread background light around the knob. In stead of using a transparent one, I designed the front panel with a white circle around the central potentiometer and a "normal" black knob, so that the colors only shine through around the edge of the knob.

I designed my front panel as a black PCB without any circuit, just using the silk layer for all graphics and texts. The central circle is just a filled white circle on the silk layer of the PCB.

<img width="400" alt="Button off" src="https://user-images.githubusercontent.com/97026614/236385844-6c81bc8c-6eac-4fa2-b61d-effbd2c706ab.jpeg">

## Additional Information about specific Components
There are several SMD components, which I listed here. Although the microcontroller does not need to be soldered separately, due to the use of the STM32F103 Blue Pill development board.
- DAC124S085 (DAC, 10-VSSOP package, the most challenging component due to its size)
- NJM4580/TL072 (OpAmp, 8-SOIC package)
- LM1117-3.3 (voltage regulator, SOT-223 package)
- LM4040B25 and LM4040B10 (voltage regulators, SOT-23-3 package)
- MMBT3904 (SMD version of the 2N3904 transistor, SOT-23-3 Package)
- 0.1uF capacitors (1608 package)

The design contains a quad VCA IC V2164 (THT version) from Cool Audio. That chip might not be available anymore. An alternative is the AS2164, available at Electric Druid or Thonk.

Concerning the resistor size, I am usually using small-size resistors, about half the length of the usual size, so they need less space on the PCB. If you want to use my Gerber files, you have to consider that fact. You might still use normal size resistors and put them in a standing position on the boards. Should also work fine.

## Firmware
I shared the .hex files for the STM32F103 chip (bootloader and main) in the folder Firmware.

The upload process is the same, as for my Braids clone. You can check out my [Braids video](https://youtu.be/TBMySGm7jKk) about how to program the Blue Pill board.

An alternative Parasite firmware version available as .wav file, which can also be uploaded via the procedure described in the official Mutable Instruments manual.

Check [this YouTube video](https://youtu.be/W8zez9X0Xok) for more details about the firmware update process.

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

## Offset CV +10V/+5V
The original design from Mutable Instruments provides the option to have a +5V offset CV for all channels, instead of +10V. This is done by a jumper setting on the module backside. I decided to skip that part and to only have the +10V offset version, since the implementation of that option would have required another dual op amp.
