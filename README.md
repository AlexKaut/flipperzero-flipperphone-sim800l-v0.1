# FlipperZero - FlipperPhone module 
FlipperPhone - diy SIM800l GPIO module for FlipperZero. All documentation for the SIM 800 l is [in the folder](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/tree/main/Schematics/SIM800L-Datasheets). 

# Module assembly
## Schematics

The first thing to start with is the SIM800L power supply. According to the specification, the module is powered by a battery, requires a voltage of 3.4-4.4 volts and can consume up to 2 amperes of current during network search! With normal activity, it consumes 20mA and only 1ma during sleep

FlipperZero has a [5 volt 2 ampere line](https://miro.com/app/board/uXjVO_LaYYI=/), so this is enough to power SIM800L. 5 volts are lowered to the required voltage using two series-connected diodes, thus, the power supply from 5 volts is organized for the blue version of the SIM800L, you can see two diodes in the upper right corner of PCB. Also, two capacitors need to be supplied along the power supply line of the GPRS module - an electrolytic 220uF and a ceramic 100n

![SIm800Lblue](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/898ec7bc-49b6-4a43-950d-aee6c6aef073)

**Lowering the voltage using two diodes is a rather unstable solution. It is very important to select diodes based on current strength and voltage drop, but even this does not guarantee a stable output voltage** 

In this board, I limited myself to a solution with two diodes, since it takes up minimal space, and the printed circuit board is single-sided and designed for home production. I didn’t encounter any critical problems during the module tests, but it’s still important to remember this point. **Write if you know convenient alternatives, please.** The advanced version of the module will have a step-down stabilizer

## PCB 
The PCB and the schematic are drawn in the EasyEDA. The current PCB is designed for self-made production, therefore, the board is one-sided, I used the toner transfer method to make my own. Blue is the lower layer, we transfer it to the textolite

![PCB2](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/50a10d77-6204-4329-8fe1-0a3240624f01)


Use the following settings for the print file

![print](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/d0382911-20ef-48d7-9f8a-c839dbcf1576)

The signature "GPRS" on the board will help not to confuse the side of the picture: 

On paper, "GPRS" should be mirrored

![side1](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/00871525-e314-4068-8640-aebecfd24419)

And on the PCB, the inscription should be read correctly

![side2](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/c5f2fa90-862e-4c68-87bf-087ce7389a84)

# FlipperPhone module control
## Connection to FlipperZero 
Put sim card in the SIM800L

![sim](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/ded0a03c-84b2-4d70-8bd3-afd6f6f51145)

Put the module in the FLipper's GPIO pins. Open "GPIO" settings and turn on "5V on GPIO". Red LED will start blinking - the module is ready

Open GPIO App "UART Terminal", choose 9600 baud rate - now you can control SIM800L with AT comands 

![9600](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/5dba9ff7-852c-48dd-b402-f770eefebd38)

## AT comands
All commands can be viewed in the [manual](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/blob/main/Schematics/SIM800L-Datasheets/SIM800L%20Series_AT%20Command%20Manual_V1.10.pdf)

List of useful commands: 
```
AT+CPAS - module status: 0 - ready to work, 2 - unknown (command execution is not guaranteed), 
3 - incoming call, 4 - voice connection

AT+CSQ - signal quality: 0 -115 dBm or less, 1 - 111 dBm, 2-30 -110..-54 dBm, 31 -52 dBm or more,
99 -unknown or no signal.

AT+CCID - getting a SIM card number

ATD+phonenumber; - call to a phone number, example of a command "ATD+79876543210;". Don't forget to put ";"!
```
**AT+CSQ**

![csq](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/56a91811-5fb8-4a60-a0c9-a0f1d8751117)

![csq27](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/f9ac00f1-6336-4ecd-8e1c-3fc9fb889956)


**ATD+phonenumber;**

![9876543210](https://github.com/AlexKaut/flipperzero-flipperphone-sim800l-v0.1/assets/86695572/5dbe3551-a5ee-47b3-91a5-e411586356cf)

