# FlipperZero - FlipperPhone module 
FlipperPhone - diy SIM800l GPIO module for FlipperZero. All documentation for the SIM 800 l is [in the folder](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/tree/main/Schematics/SIM800L-Datasheets). 

# Module assembly
## Schematics
The first thing to start with is the SIM800L power supply. According to the specification, the module is powered by a battery, requires a voltage of 3.4-4.4 volts and can consume up to 2 amperes of current during network search! With normal activity, it consumes 20mA and only 1ma during sleep

FlipperZero has a [5 volt 2 ampere line](https://miro.com/app/board/uXjVO_LaYYI=/), so there are no problems with power supply. 5 volts are lowered to the required voltage using two series-connected diodes, thus, the power supply from 5 volts is organized for the blue version of the SIM800L, you can see two diodes in the upper right corner of PCB. Also, two capacitors need to be supplied along the power supply line of the GPS module - an electrolytic 220uF and a ceramic 100n

![SIm800Lblue](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/898ec7bc-49b6-4a43-950d-aee6c6aef073)


## PCB 
The PCB and the schematic are drawn in the EasyEDA. The current PCB is designed for self-made production, therefore, the board is one-sided, I used the toner transfer method to make my own. Don't forget to solder the jumer!!! Blue is the lower layer, red is the upper layer. We transfer the blue to the textolite, and solder the red track as a jumper

![PCB](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/2d756ae5-2529-473b-b3e0-5352bc1ab734)

Use the following settings for the print file

![print](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/d0382911-20ef-48d7-9f8a-c839dbcf1576)

The signature "GPRS" on the board will help not to confuse the side of the picture: 

On paper, "GPRS" should be mirrored

![side1](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/00871525-e314-4068-8640-aebecfd24419)

And on the PCB, the inscription should be read correctly

![side2](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/c5f2fa90-862e-4c68-87bf-087ce7389a84)


