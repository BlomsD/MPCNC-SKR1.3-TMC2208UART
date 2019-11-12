# MPCNC-SKR1.3-TMC2208UART
Modified Marlin 2.0 firmware for the BigTreeTech SKR1.3 with TMC2208 UART drivers for the MPCNC. Includes dual end stops.

Features:
* Compatibility with <a href="https://www.aliexpress.com/item/32978749024.html?spm=a2g0s.9042311.0.0.27424c4d3UaNlG">SKR1.3 from BigTreeTech</a>
* Immediate compatibility with TMC2208 in UART mode with Stealthchop and driver monitoring enabled
* Works with the MPCNC with 5 motors via 5 stepper drivers and with end stops enabled
* Marlin M122 enabled to allow diagnostics of TMC drivers
* Babystepping is enabled to allow slight Z changes when running a project
* Uses the heated bed pins as the "fake" extruder (so these are not available for use)

Possible changes to use with your MPCNC:
Marlin\configuration.h
* If you have 3 wire end stops or your end stop isn't working as expected in Marlin\configuration.h change true/false on the appropriate ENDSTOP_INVERTING from lines 639 to 645
* If you have a 16tooth pulley then you are good to go. If you have a 20 tooth then edit line 720 to have the values of 80, 80, 400, 80
* You can change X_BED_SIZE and Y_BED_SIZE on lines 1054 and 1055 to match your cutting area to assist the firmware with not allowing you to crash once homed (I have not gotten software max endstops to work perfectly yet)
Marlin\Configuration_adv.h
* If your motors aren't moving the axis the same direction go change INVERT_X2_VS_X_DIR or INVERT_Y2_VS_Y_DIR from true to false (or flip the motor wires). If both motors are working as they should but going the wrong way check lines 1022-1024 in Configuration.h (or flip the motor wires)

To use:
* Download all the files
* Open as a PlatformIO project in either Atom or Microsoft VSCode
* Make edits as required
* Build or build/upload the project
* Install microsd card in the SKR1.3 if you didn't directly upload and then reset the SKR1.3

Source info:
* Firmware is based on Ryan's <a href="https://www.v1engineering.com/marlin-firmware/">original MPCNC firmware</a> from V1Engineering 
* The version of Marlin 2.0.X used is "414D bugfix-2.0.x" from "2019-10-18".
* Thanks to <a href="https://www.youtube.com/channel/UCbgBDBrwsikmtoLqtpc59Bw">TeachingTech</a> for info on the SKR1.3 and pins.

Changelog:
* 12NOV2019 - V1.0.0 - Initial public release
