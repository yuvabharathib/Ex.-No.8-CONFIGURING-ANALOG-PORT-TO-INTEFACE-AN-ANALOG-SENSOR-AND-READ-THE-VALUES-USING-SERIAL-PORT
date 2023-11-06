 


### Ex. No. :8 CONFIGURING ANALOG PORT TO INTEFACE AN ANALOG SENSOR AND READ THE VALUES USING SERIAL PORT
## Date: 
###  

## Aim: 
To configure internal ADC for interfacing an analog sensor and read the values on the com port 
## Components required:
STM 32 CUBE IDE , STM32 NUCLEO BOARD, CONNECTING CABLE, SERIAL PORT UTILITY 
 ## Theory 

Potentiometer and ADC. Image by author.
Analog-to-Digital Converter: the basics
If you have a microphone the audio it picks up is analog. As explained before, you can use an ADC to move from real-world analog to software-friendly digital signals.

ADCs are characterized by:

Resolution [bit]: the number of bits to represent a digital signal.
Sampling rate [Hz]: how fast they work.

ADC Symbol. 
An 10-bit ADC with 1 kHz sampling rate has 256 (2⁸) levels in its digital signal and takes 1 millisecond to convert an analog signal into its digital form.
![image](https://github.com/vasanthkumarch/Ex.-No.8-CONFIGURING-ANALOG-PORT-TO-INTEFACE-AN-ANALOG-SENSOR-AND-READ-THE-VALUES-USING-SERIAL-PORT/assets/36288975/bdbe1fe6-6913-46ca-aefd-726b6a406cf6)

An analog signal is expressed in voltage [V] and other important features are:

Full-scale voltage: the maximum input voltage value convertible into digital.
Voltage resolution (Quantum): equal to its full-scale voltage divided by the number of levels.
An 8-bit ADC with 3.3V of full-scale voltage has a quantum equal to: 3.3V / 256 levels = 12.9mV.
The quantum is the minimum voltage value that ADC can discretize. When an analog value being sampled falls between two digital levels the analog signal will be represented by the nearest digital value. This causes a very slight error called “quantization error”.

The STM32 Nucleo Board
The STM32 development board in use belongs to the NUCLEO family: the NUCLEO-G431RB is equipped with an STM32G431RB microcontroller, led, buttons, and connectors (Arduino shield compatible). It provides an easy and fast way to build prototypes.


STM32 NUCLEO-G431RB development board.  
The STM32G071RB is a mainstream ARM Cortex-M4 microcontroller with 128KB flash memory, most common communication interfaces (I2C, SPI, UART, …), and peripherals (ADC, DAC, PWM, Timer, …).



Potentiometer pinout.  
The output signal will be connected to one of the 6 analog inputs of the NUCLEO board (marked with Ax). VCC and GND will be connected to the power section of the board: 3.3V and GND, respectively.


  
 ## Procedure:

Open STM32CubeIDE Software and go to File → New… → STM32 Project.
Click on Board Selector and select NUCLEO-G431RB in the dropdown menu.

Board selector section. Image by author.
Insert a project name and select STM32Cube as Targeted Project Type.

Setup STM32 project. Image by author.
After creating the project, a page will appear showing all the necessary features needed to configure the MCU.

STM32Cube device configuration. 
The STM32G071RB has 2 ADCs (named ADC1 and ADC2) with a maximum sampling rate of 4MHz (0.25us) and up to 19 multiplexed channels. Resolution of 12-bit with a full-scale voltage range of up to 3.6V.
With channels, it is possible to organize the conversions in a group. A group consists of a sequence of conversions that can be done on any channel and in any order, also with different sampling rates.

The Analog connector of the development board is connected to pins: PA0, PA1, PA4, PB0, PC1, and PC0 of the microcontroller.
![image](https://github.com/vasanthkumarch/Ex.-No.8-CONFIGURING-ANALOG-PORT-TO-INTEFACE-AN-ANALOG-SENSOR-AND-READ-THE-VALUES-USING-SERIAL-PORT/assets/36288975/152f51fd-f09b-4d65-8744-9492c86f1720)

Pinout of the analog connector — NUCLEO-G071RB. .
The potentiometer is wired to the PA0 pin and so the ADC1 Channel 0 (ADC1_IN0) will be used to convert the analog value.

Open the Pinout&Configuration tab and click on Analog → ADC1 in the Categories section.
In the channel 1 (IN0) dropdown menu select Single-ended.
The ADC can be configured to measure the voltage difference between one pin and the ground (Single-ended configuration) or between two pins (Differential configuration).
![image](https://github.com/vasanthkumarch/Ex.-No.8-CONFIGURING-ANALOG-PORT-TO-INTEFACE-AN-ANALOG-SENSOR-AND-READ-THE-VALUES-USING-SERIAL-PORT/assets/36288975/84e5114c-ff8b-4058-8ad7-760bcf06f931)

ADC1 mode panel.  
Leave the ADC1 Configuration panel with the default values and save the project.
* Clock prescaler: Synchronous clock mode divided by 4
ADC Clock derives from the system clock (SYCLK) that is set to the maximum frequency: 170MHz.
Divide by 4 means to set the maximum ADC sampling frequency (170MHz/4 = 42.5MHz).
* Resolution: ADC 10-bit resolution
Output digital signal has 1024 levels. The voltage full-scale range is equal to the microcontroller supply voltage (3.3V).

ADC1 configuration panel.  .
After saving the configuration, the STM32CubeIDE will generate all the project files according to the user inputs.




##  Program 


 

## Result :
 
## Output screen shots :






