# end_node_mamwle

## Description

Implementation of LoRaWAN end node example project for MAMWLE module using source code generated by STM32CubeMX (firmware package ver 1.2 for STM32WL family).

The example is set for sending a 1-byte payload on port 2 every 10 seconds. The 1-byte payload starts from 0 and goes up to 255 and is incremented by one at each packet transmission.

All the settings can be found within the .ioc file. LoRaWAN configuration can be customized from within STM32CubeMX software using the parameters located in _"Pinout & Configuration"_ tab / _"Middleware"_ category / LORAWAN.

It is possible for the user to edit the STM32CubeMX project settings and regenerate the source code: the customization is done in a way that makes them unaffected by code regeneration. 

## How to generate the project from scratch

1. Open the included .ioc file with STM32CubeMX, set the options as needed and generate code to an empty folder.

2. Generated code will not compile because BSP files are missing. Add the BSP folder inside _"project_root/Drivers"_, this folder includes the following files:

   - _stm32wlxx_nucleo.h_: dummy file for fixing reference by STM32CubeMX genetared code and avoid compile error.

   - _stm32wlxx_nucleo_errno.h_: copied as-is from ST's project "LoRaWAN_End_Node" for NUCLEO-WL55JC.

   - _stm32wlxx_nucleo_radio.c_: copied as-is from ST's project "LoRaWAN_End_Node" for NUCLEO-WL55JC.

   - _stm32wlxx_nucleo_radio.h_: copied as-is from ST's project "LoRaWAN_End_Node" for NUCLEO-WL55JC.

   These files won't be deleted by a new code generation with STM32CubeMX.

3. Open the project with STM32CubeIDE and inside project's properties go to _"C/C++ Build"_ / "_Build_" / _"MCU GCC Compiler"_ / _"Include paths"_ and, for each build configuration, add the row _"../Drivers/BSP"_ for including the new BSP folder.

4. Add code to lora_app.c for printing join status and sending example data packets: payload is 1 byte long, starts from 0 and is incremented at each transmission. This code is added under user code sections and is preserved in case code is generated again with STM32CubeMX.

## Software version

- STM32CubeMX version 6.6.1
- STM32CubeWL Firmware Package V1.2.0
- STM32CubeIDE version 1.10.1
