<picture>
    <source media="(prefers-color-scheme: dark)" srcset="images/microchip_logo_white_red.png">
	<source media="(prefers-color-scheme: light)" srcset="images/microchip_logo_black_red.png">
    <img alt="Microchip Logo." src="images/microchip_logo_black_red.png">
</picture> 

## MATLAB SIP dsPIC33CDVL64MC106 FOC with SMO and Field Weakening

## 1. INTRODUCTION
<p style='text-align: justify;'>
This document describes the setup requirements for running the Sensorless FOC with field weakening algorithm and a Sliding Mode Observer (SMO), using MATLAB/Simulink and dsPIC33CDVL64MC106 Motor Control Development Board.</p>
<p style='text-align: justify;'>
The SMO implementation is referenced from AN1078 “Sensorless Field Oriented Control of a PMSM”.
</p>

## 2.	SUGGESTED DEMONSTRATION REQUIREMENTS
### 2.1 MATLAB Model Required for the Demonstration
-  MATLAB model can be cloned or downloaded as zip file from the Github repository ([link](https://github.com/microchip-pic-avr-solutions/matlab-sip-mc-dspic33cdvl64mc106-foc-smo)).

### 2.2	Software Tools Used for Testing the MATLAB/Simulink Model
1.	MPLAB X IDE and IPE (v6.20)
2.	XC-DSC compiler (v3.00)
3.	MATLAB R2023b
4.	Required MATLAB add-on packages
    -	Simulink (v23.2)
    -	Simulink Coder (v23.2)
    -	Stateflow (v23.2)
    -	MATLAB Coder (v23.2)
    -	Embedded Coder (v23.2)
    -	MPLAB Device blocks for Simulink (v3.54)
    - Motor Control Blockset (v23.2)

> **_NOTE:_**
>The software used for testing the model during release is listed above. It is recommended to use the version listed above or later versions for building the model.

### 2.3	Hardware Tools Required for the Demonstration
- dsPIC33CDVL64MC106 Motor Control Development Board ([EV04R09A](https://www.microchip.com/en-us/development-tool/ev04r09a))
- 24V Power Supply ([AC002013](https://www.microchipdirect.com/dev-tools/AC002013)) 
- 24V, 3-Phase Brushless DC Permanent Magnet Hurst Motor ([AC300022](https://www.microchip.com/en-us/development-tool/AC300022))

> **_NOTE:_**
>All items listed under this section Hardware Tools Required for the Demonstration are available at [microchip DIRECT](https://www.microchipdirect.com/).

  
## 3. HARDWARE SETUP
This section describes hardware setup required for the demonstration.

1. The blue color power-on LED (LD4) indicates the device dsPIC33CDVL64MC106 is populated on the development board

     <p align="left" >
     <img  src="images/boardname.PNG"></p>

2. Connect the 3-phase wires from the motor to PHC, PHB, and PHA of the **connector J10**(no specific order), provided on the dsPIC33CDVL64MC106 Motor Control Development Board.

     <p align="left" >
     <img  src="images/motorconnection.png"></p>

3. Plug the 24V power supply to **connector J1** on the dsPIC33CDVL64MC106 Motor Control Development Board. Alternatively, the development board can also be powered through connector J2.

     <p align="left" >
     <img  src="images/boardpower.png"></p>
 
4. The board has an onboard programmer **PICkit™ On Board (PKoBv4)** , which can be used for programming or debugging the microcontroller or dsPIC DSC on the development board. To use the onboard programmer, connect a micro-USB cable between the Host PC and **connector J12** on the dsPIC33CDVL64MC106 Motor Control Development Board.

     <p align="left" >
     <img  src="images/boardpkob.png"></p>

5. Alternatively, connect the Microchip programmer/debugger MPLAB® PICkit™ 4 In-Circuit Debugger between the Host PC used for programming the device and the **ICSP header J6** on the dsPIC33CDVL64MC106 Motor Control Development Board (as shown). Ensure that PICkit 4 is oriented correctly before proceeding.

     <p align="left" >
     <img  src="images/boardpickit.PNG"></p>
 
 </br>

## 4.	BASIC DEMONSTRATION
<p style='text-align: justify;'> Follow the below instructions step-by-step, to set up and run the motor control demo application:</p>

1. Launch MATLAB (refer the section [“2.2 Sofware Tools Used for Testing the MATLAB/Simulink Model"](#22-software-tools-used-for-testing-the-matlabsimulink-model)).</p> 
2. Open the folder downloaded from the repository, in which MATLAB files are saved (refer the section ["2.1 MATLAB Model Required for the Demonstration"](#21-matlab-model-required-for-the-demonstration)).

    <p align="left" >
    <img  src="images/dem1.png"></p>

3.	<p style='text-align: justify;'> Double click and open the .m file. This .m file contains the configuration parameter for the motor and board. By default, the .m file is configured to run Hurst 300 motor and LVMC board. Run the file by clicking the <b>“Run”</b> icon and wait till all variables gets loaded on the <b>‘Workspace’</b> tab.

    <p align="left">
      <img  src="images/dem2.png"></p>
    </p>

4.	<p style='text-align: justify;'>Double click on the Sensorless FOC Simulink model.

    <p align="left">
      <img  src="images/dem3.png"></p>
    </p>

5.	<p style='text-align: justify;'>This opens the Simulink model as shown below. Click on the <b>"Run"</b> icon to start the simulation.

    <p align="left">
      <img  src="images/dem4.png"></p>
    </p>

6.	<p style='text-align: justify;'>To plot the simulation result, <b>Data Inspector</b> is used (refer to figure below). To observe the additional signals, log them as required. Alternatively, normal Simulink Scope can be used to plot the signals.

    <p align="left">
      <img  src="images/dem5.png"></p>
    </p>

7.	<p style='text-align: justify;'>From this Simulink model an MPLAB X project can be generated, and it can be used to run the PMSM motor using LVMC board. <p style='text-align: justify;'>To generate the code from the Simulink model, go to the <b>"MICROCHIP"</b> tab, and enable the tabs shown in the figure below. 

    <p align="left">
      <img  src="images/dem7.png"></p>
    </p>

8.	<p style='text-align: justify;'>	To generate the code and run the motor, click on <b>‘Build Model’ or ‘Clean Build Model’</b> option under the <b>“Microchip”</b> tab. This will generate the MPLAB X project from the Simulink model and program the dsPIC33CK256MP508 device.

    <p align="left">
      <img  src="images/demo8.png"></p>
    </p>

9.	<p style='text-align: justify;'>After completing the process, the <b>‘Operation Succeeded’</b> message will be displayed on the <b>‘Diagnostics Viewer’</b>.

    <p align="left">
      <img  src="images/dem9.png"></p>
    </p>

10.	If the device is successfully programmed, <b>LED1 - LD1</b> will be blinking and the <b>LED2 - LD2</b> will be OFF.

    <p align="left">
      <img  src="images/led.png"></p>
    </p>

11.	To Run the motor, press the push button <b>SW1</b>.

    <p align="left">
      <img  src="images/pushbutton.png"></p> 
    </p>

12.	The motor speed can be varied using the potentiometer (labeled <b>“POT1”</b>). Approximately, after 70% of the full potentiometer value (approximately at 3000 RPM), the motor enters into field weakening region.

    <p align="left">
      <img  src="images/potentiometer.png"></p>
    </p>

13.	Press the push button <b>SW1</b> to stop the motor. Make sure motor is reduced minimum potentimeter value before stopping the motor.

    <p align="left">
      <img  src="images/pushbutton.png"></p>
    </p>

> **_NOTE:_**
>The LED2 is connected to the Fault pin of the Gate Driver of the dsPIC33CDVL64MC106 device. If any gate driver fault occurs this LED will be turned ON.
> To reset this fault, the pushbutton SW3 has to be pressed. Once fault is reset, the LED2 will be turned OFF.

## 5.	DATA VISUALIZATION USING MOTOR CONTROL BLOCKSET (MCB) HOST MODEL
<p style='text-align: justify;'>The Sensorless FOC model comes with the initialization required for data visualization using Motor Control Blockset Host Model (MCB Host Model). The MCB Host Model is a Simulink model which facilitates data visualization through the UART Serial Interface. 

1.	<p style='text-align: justify;'>To establish serial communication with the host PC, connect a micro-USB cable between the host PC and the dsPIC33CDVL64MC106 Motor Control Development Board (J12 connector). This interface is used for programming as well. 

    <p align="left">
      <img  src="images/boardpkob.png"></p>
    </p>

2. Ensure the sensorless FOC model is programmed and running as described under section ["4. Basic Demonstration"](#4-basic-demonstration) by following steps 1 through 13.

3. <p style='text-align: justify;'>Open the MCB Host model and double click on the <b>“Serial Setup”</b> block. Then select the appropriate COM port connected to the hardware from the drop-down menu and set the baud rate as 460829. Please note that the same baud rate is required to be chosen in the Sensorless FOC model (the baud rate can be viewed on the <b>“UART Configuration”</b> block inside <b>“MOTOR CONTROL DEVLOPMENT BOARD  Template”</b>).

    <p align="left">
      <img  src="images/host3.png"></p>
    </p>

4.	<p style='text-align: justify;'>Open the <b>“UART_Rx”</b> subsystem to configure the COM port. This can be done by configuring the <b>“Host Serial Receive”</b> block of the “UART_Rx” subsystem. Ensure to select the same COM port configured in step 3. 

    <p align="left">
      <img  src="images/host4.png"></p>
    </p>

5.	<p style='text-align: justify;'>Click the run icon of the MCB Host model to open the scope window and monitor the signals.

    <p align="left">
      <img  src="images/host5.png"></p>
    </p>

6.	<p style='text-align: justify;'>In the figure below, one example is shown where two signals (estimated and reference speeds) have been plotted.

    <p align="left">
      <img  src="images/host6.png"></p>
    </p>


## 	REFERENCES:
For more information, refer to the following documents or links.
1.	AN1078 Application Note “[Sensorless Field Oriented Control of a PMSM](https://www.microchip.com/en-us/application-notes/an1078)”.
2.	dsPIC33CDVL64MC106 and dsPIC33CDV64MC106 Motor Control Development Boards User’s Guide  ([DS50003060](https://ww1.microchip.com/downloads/aemDocuments/documents/MCU16/ProductDocuments/UserGuides/dsPIC33CDVL64MC106-and-dsPIC33CDV64MC106-Motor-Control-Development-Boards-Users-Guide-DS50003060.pdf)) 
3. [MPLAB® X IDE installation](https://microchipdeveloper.com/xwiki/bin/view/software-tools/x/install-guide/)
4. [MPLAB® XC-DSC Compiler installation](https://microchipdeveloper.com/xwiki/bin/view/software-tools/xc-dsc/install/)
5.  [Motor Control Blockset](https://in.mathworks.com/help/mcb/)
6.  [MPLAB Device Blocks for Simulink :dsPIC, PIC32 and SAM mcu](https://in.mathworks.com/matlabcentral/fileexchange/71892-mplab-device-blocks-for-simulink-dspic-pic32-and-sam-mcu)