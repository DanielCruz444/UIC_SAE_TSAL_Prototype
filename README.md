# UIC_SAE_TSAL_Prototype

This repository includes files for a 72V TSAL prototype that was created for the Formula E team at University of Illinois Chicago during the 2023-2024 school year. Ideas were borrowed from Michael Ruppe's TSAL design. Many thanks to him! Link to his youtube video: https://www.youtube.com/watch?v=bgW9xbbovIY

The files named "SAE_TSALPCB_PROTO (6-18-2024 12-38-47 PM).zip" and "TSAL_LEDs (6-18-2024 12-40-12 PM).zip" are the files for the main TSAL board and LEDs board on Altium, respectively. When opening the files, error messages might pop up saying the gerber files are not in the zip file, however this is just a file packaging issue as the gerber files are included in the zip file. The file named "sae_tsalpcb_proto-2024-06-18T17-56.zip" includes the Pspice for TI simulation file. The circuit was simulated on Pspice for TI before testing on a breadboard to ensure any bugs were dealt with and to ensure that the circuit was safe to test (in theory). Some components such as the power supplies, DC-DC converter, and LEDs were generalized or not included in the simulation file due to them not having simulation models. However, this did not have a major impact during breadboard testing. Pspice for TI was used because some Texas Instruments components would not simulate correctly on Altium. Some component simulation models may be restricted to only work with certain softwares. Link on how to get started with Pspice for TI: https://www.ti.com/video/series/explore-pspice--for-ti-design-and-simulation-tool.html

Description of Project:
The purpose of this project was to develop a circuit that would connect to the input node of the Formula E car's motor controller in order to indicate whether it had been precharged to 60Vdc or higher (considered high voltage according to FSAE). In other words, it would show when high voltage was present outside the high voltage battery pack and running through the car's tractive system. If the voltage at the motor controller's input node was detected to be less than 60Vdc, solid green LEDs would be lit. If a voltage of 60Vdc or higher was detected, red LEDs would be flashing at a frequency of 3Hz.

Development Details:
*Redesigned and simulated a Tractive System Active Light circuit schematic using PSpice for TI on Cadence.
-Researched different types of components and read their datasheets in order to design a circuit with components that worked together.
-Involved importing and configuring simulation models for components and then producing simulation profiles to view waveforms based on probe placements (voltage, current, power markers).
-Emphasized circuit schematic neatness and net naming in order to improve readability for self and teammates.
-Evaluated component variations, made bill of materials (BOM), and ordered on Mouser.
-Tested and validated circuit on a breadboard using power supplies, oscilloscope, and multimeter.

*Designed Tractive System Active Light pcb and LED pcb layouts using Altium
-Main circuit had to be in an electronics enclosure at the rear of the car and the LEDs of the circuit had to be at the front of the car, so two seperate but connected pcbs were designed.
-To connect inputs and outputs for the two pcbs, microfit 3.0 connectors were used. Crimping and soldering ensued.

Description of jpg images:
"TSAL_Main_1.jpg"-Picture of main TSAL board assembled.
"TSAL_Secondary_1.jpg"-Picture of LED board assembled.
"TSAL_Main_Altium.jpg"-This is the TSAL Main PCB designed. It is the "Main" PCB of the project as it has all of the main components assembled on it. The secondary PCB has the LEDs assembled on it. Note: The color of this PCB was chosen as red since the team wanted to make it clear that high voltage would be present on this board and extra care would need to be considered when handling it.
"TSAL_Secondary_Altium.jpg"-This is the LED PCB of the project. This board has the LEDs assembled on it and would be located in a separate location to the "Main" TSAL PCB. The board was made green and not red as it only contains low voltage from the car's low voltage battery.
"TSAL_PspiceForTI_Simulation_High.jpg"-This is the simulation result when the TSAL has an input greater than 60 Vdc. The green curve represents the voltage the green LEDs would encounter when a p channel mosfet conducts. As a result they will not conduct. The red curve represents the voltage the red LEDs would encounter when an n channel mosfet will conduct. As a result, they will flash with a frequency of 3 Hz.
"TSAL_PspiceForTI_Schematic_High.jpg"-This is the schematic of the TSAL that was simulated on Pspice For TI. In the high state, the high voltage input is greater than 60 Vdc.
"TSAL_PspiceForTI_Simulation_Low.jpg"-This is the simulation result when the TSAL has an input of less than 60 Vdc. The green curve represents the voltage the green LEDs would encounter when a p channel mosfet conducts. As a result they will light up solidly. The red curve represents the voltage the red LEDs would encounter when an n channel mosfet will not conduct. As a result, they will not light up. There is no voltage drop across the red LEDs.
"TSAL_PspiceForTI_Schematic_Low.jpg"-This is the schematic of the TSAL that was simulated on Pspice For TI. In the low state, the high voltage input is less than 60 Vdc.
