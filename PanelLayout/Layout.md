## Panel Layout for PCB

The panel dimensions provided in the section "Original Design" below are based on my own module build, since I am not following the standard HP (1HP eq. 5.08mm) size. An alternative by building an HP-standard size panel can be found in the section "HP Standard Design" further below.

### Original Design
Coordinates given in the table fit to the layout of components given in the PCBc in folder GerberFiles.
The layout is the same for both versions.

Panel size: 75mm x 128.5mm

The numbers in the table are refering to the numbers in the picture below.
Coordinates origin is the lower left corner of the panel.


| No. | X-coord. [mm] | Y-coord. [mm] | Comment |
| --- | --- | --- | --- |
| 1 | 10.5 | 105 | Channel 1 Pot |
| 2 | 28.5 | 105 | Channel 2 Pot |
| 3 | 46.5 | 105 | Channel 3 Pot |
| 4 | 64.5 | 105 | Channel 4 Pot |
| 5 | 10.5 | 89 | LED |
| 6 | 28.5 | 89 | LED |
| 7 | 46.5 | 89 | LED |
| 8 | 64.5 | 89 | LED |
| 9 | 12 | 76 | Add Button |
| 10 | 12| 68 | LED |
| 11 | 12 | 60 | Delete Button |
| 12 | 37.5 | 79 | RGB LED |
| 13 | 37.5 | 68 | Frame Pot|
| 14 | 37.5 | 57 | RGB LED |
| 15 | 64.5 | 50 | Modulation CV Attenuverter Pot |
| 16 | 10 | 40 | Offset CV Switch |
| 17 | 10 | 30 | Sum Input Jack |
| 18 | 21 | 30 | Input 1 Jack |
| 19 | 32 | 30 | Input 2 Jack |
| 20 | 43 | 30 | Input 3 Jack |
| 21 | 54 | 30 | Input 4 Jack |
| 22 | 65 | 30 | Modulation CV Jack |
| 23 | 10 | 15 | Mix Output Jack |
| 24 | 21 | 15 | Output 1 Jack |
| 25 | 32 | 15 | Output 2 Jack |
| 26 | 43 | 15 | Output 3 Jack |
| 27 | 54 | 15 | Output 4 Jack |
| 28 | 65 | 15 | Frame Step Output Jack |

<img height="1200" src="https://user-images.githubusercontent.com/97026614/236418343-ae0b6b7f-3c15-4cfd-9008-c1947dfc336c.png"> 

### HP Standard Design
For building the panel with a size following the HP standard, you can use the panel Gerber file provided in the folder "GerberFiles".
I ordered my own panel via such gerber file built out of PCB material.

Here are a few parameters of the panel.
| Parameter | Value |
| --- | --- |
| Width | 16HP |
| Pot hole diameter | 8mm |
| Jack hole diameter | 6.1mm |
| Toggle switch hole diameter | 6.5mm |
| Tact switch hole diameter | 5.1 mm |
| LED hole diameter | 3.1mm|
| Mounting hole diameter | 3.2mm|
