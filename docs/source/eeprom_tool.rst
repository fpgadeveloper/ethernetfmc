.. _eeprom-tool:

===============
FMC EEPROM Tool
===============

Description
===========

The Opsero FMC EEPROM Tool can be used to verify the EEPROM contents of Opsero FMC products
using an FPGA or MPSoC board such as the ZCU102 or VCU118 board. The tool can also be used
to reprogram the EEPROM in the case that it was mistakely erased or corrupted. 

.. :WARNING:: Only use this tool with Opsero FMC products. The use of this tool with
	            FMCs from other	manufacturers is strictly prohibited and may result in
	            damage to the FMC or to the carrier board.

Supported boards
================

The tool currently supports the following FPGA/MPSoC boards. You must have at least one of
these boards in order to use the tool.

* ZedBoard
* ZCU102 Rev1.0 and Rev1.1
* KC705
* VCU118
* ZCU104

Download
========

The tool can be downloaded at the link below:

`Opsero FMC EEPROM Tool v1.3 <https://opsero.com/downloads/opsero_fmc_eeprom_tool_v1_3.zip>`_

The zip file contains a boot file (bitstream or BOOT.bin) for each of the supported boards.

Usage instructions
==================

To run the tool, follow these steps:

#. Plug the FMC card you wish to reprogram into one of the FMC 
   connectors of your FPGA/MPSoC board. The tool is designed to probe
   all of the FMC connectors on the FPGA/MPSoC board.
	
#. If you are using the ZedBoard, be sure to set the VADJ jumper setting
   to 1.8V. If you are using the KC705, be sure that your FMC card can
   support	a VADJ of 2.5V, which is the default setting of that board.
	
#. Connect the UART of your FPGA/MPSoC board to a PC.
	
#. For Zynq and Zynq MP boards, a BOOT.bin file is provided. Copy this
   file to your board's SD card and configure it to boot from SD card.
   Then plug the SD card back into the board and power it up.
	
#. For FPGA boards, a bitstream is provided with an embedded ELF file.
   Power up your FPGA/MPSoC board and then download the bitstream to the
   FPGA board using the Vivado Hardware Manager tool.
	
#. Open a terminal program such as Putty and connect to the serial port
   of your FPGA/MPSoC board. If you see nothing in the terminal window,
   press ENTER to redisplay the menu.
	
#. Use the menu options to do the following:

  (p) **Program the EEPROM**
      
      You will be asked to select the FMC product from a list, and also to
      enter the product's serial number. Note that entering incorrect
      information here can lead to your FMC card being damaged by a VADJ
      voltage that is greater than it's true rating. If you are not
      sure about the product to select here, please contact Opsero first.
  	
  (a) **Add a spacer**
      
      For 2-byte address EEPROMs only. This option allows you to add a 
      spacer byte before the IPMI FRU data on the EEPROM. This can be used
      to help some FPGA/MPSoC boards to properly read 2-byte address 
      EEPROMs. See below for an explanation.
  
  (r) **Remove the spacer**
      
      For 2-byte address EEPROMs only. This option allows you to remove a
      spacer byte from the EEPROM.


Use of the spacer
=================

As referred to in this document and by the tool, a "spacer" is simply a
single byte that is inserted into the EEPROM at address 0x00 and preceeding
the IPMI FRU data.

In order to understand the purpose of the spacer, it is necessary to 
understand the two types of I2C EEPROM: 1-byte address and 2-byte address
EEPROMs (also known in industry as "standard" and "smart serial" EEPROMs).
The difference between these EEPROMs comes down to how many	bytes are sent
by the I2C master to specify the address from which it wants to read, or to
which it wants to write.

After locating an EEPROM, the first thing that this tool does is determine 
if the EEPROM uses an address field of 1-byte or 2-bytes. This information is 
displayed in the EEPROM status of the main menu.

The VITA 57.1 standard specifies that FMC cards should have an EEPROM with an 
address field of 1-byte. FPGA/MPSoC boards are thus designed to communicate 
with a 1-byte address EEPROM on the FMC card. Communication issues can arise 
when using FMC cards that deviate from the standard and have a 2-byte address 
EEPROM. In this configuration, the FPGA/MPSoC board will send I2C commands 
with a 1-byte address field, but the EEPROM is expecting a 2-byte address field.

At first glance, this incompatibility seems like a big problem, but in fact
we can work around it because the master's interaction with the EEPROM is minimal.
The FPGA/MPSoC board only needs to read from the FMC's EEPROM, not write to it.
When only reading from an I2C EEPROM, it actually doesn't matter if the EEPROM
has a 1-byte or a 2-byte address field. This is because the read command doesn't 
have an address field. Instead, a read command returns data starting from the
address pointed to by the internal address register in the EEPROM. As each byte
is read from the EEPROM, the internal address register increments by one.

Typically, the I2C master would prepare for reading an EEPROM by first setting the
internal address register to the address that it wants to read from. To set the
internal address register, the master sends a write command containing an address
field set to the desired value. If the master device only sends one byte for the 
address, a 2-byte address EEPROM would ignore the write request, considering it 
to be incomplete. Luckily in our case, this is inconsequential, because the IPMI 
FRU data starts from address ZERO, and the internal address register defaults to 
ZERO on power-up.

So why is there even a problem? Well, it turns out that some FPGA/MPSoC boards 
start off by sending a read command, and reading just one byte. This is probably 
done just to make sure that an EEPROM is actually connected. This initial single 
byte read causes the internal address register to be incremented to ONE. After the 
initial read, the master then tries to set the internal address register to ZERO 
and proceeds to read the entire EEPROM. As explained earlier, the master will fail 
at setting the internal address register, so it will remain pointing at address ONE
and the IPMI FRU data will be read out starting from the second byte (ie. it will
be missing the first byte).

By adding a dummy byte (spacer) to the beginning of the EEPROM, we can ensure that
the IPMI FRU data is correctly read by the master.

Note that not all FPGA/MPSoC boards are programmed to send an initial single-byte
read command on start-up, so they don't all need the spacer. The KCU105 board is
one example of this.


When to use the spacer
======================
	
If your FMC card has a 1-byte address EEPROM, this tool will NOT give you the
option to add or remove a spacer, as you will have no need for one. All 
FPGA/MPSoC boards should be able to read 1-byte address EEPROMs on the FMC 
card as per	the VITA 57.1 standard.

If your FMC card has a 2-byte address EEPROM, this tool will give you the 
option to add or remove a spacer in your FMC's EEPROM. Adding a spacer can allow
some FPGA/MPSoC boards to properly read a 2-byte address EEPROM.

A spacer has been found to work with the following boards:

* ZCU102
* ZCU102-ES2
* VCU118

The following boards will work without the spacer:

* KCU105
	
If your FPGA/MPSoC board is not listed above and is not applying VADJ to your FMC
card, then try adding or removing the spacer. If your board is not applying
VADJ regardless of the spacer being there or not, please contact Opsero.


