==============
Specifications
==============

Recommended Operating Conditions
================================

+-------------------+------------------------+------------+------------+-----------+--------+
|                                            | MIN        | TYP        | MAX       | UNIT   |
+===================+========================+============+============+===========+========+
| Supply voltage    | 12 VDC                 |    +11.4   |    +12     |    +12.6  |    V   |
|                   +------------------------+------------+------------+-----------+--------+
|                   | 3.3 VDC                |    +3.14   |    +3.3    |    +3.46  |    V   |
|                   +------------------------+------------+------------+-----------+--------+
|                   | VADJ 2.5VDC            |    +2.38   |    +2.5    |    +2.62  |    V   |
|                   +------------------------+------------+------------+-----------+--------+
|                   | VADJ 1.8VDC            |    +1.71   |    +1.8    |    +1.89  |    V   |
+-------------------+------------------------+------------+------------+-----------+--------+

Power Consumption
=================

The specifications below refer to the total current draw on each of the power supplies while
the Ethernet FMC is connected to a development board and operating at 100% channel utilization.

+-------------------+-----------------+-------------+------------+------------+-----------+--------+
|                   | SUPPLY          | UTILIZATION | MIN        | TYP        | MAX       | UNIT   |
+===================+=================+=============+============+============+===========+========+
| Current draw      | 12 VDC          |   100%      |            |    0       |           |   mA   |
|                   +-----------------+-------------+------------+------------+-----------+--------+
|                   | 3.3 VDC         |   100%      |            |    740     |           |   mA   |
|                   +-----------------+-------------+------------+------------+-----------+--------+
|                   | VADJ 2.5 VDC    |   100%      |            |    144     |           |   mA   |
|                   +-----------------+-------------+------------+------------+-----------+--------+
|                   | VADJ 1.8 VDC    |   100%      |            |    144     |           |   mA   |
+-------------------+-----------------+-------------+------------+------------+-----------+--------+

* Tests performed at ambient temperature of 25 degrees C
* Tests performed using IP in the FPGA to generate the Ethernet packets

Note that Ethernet FMC usage will typically produce an increase in power consumption 
of the FPGA on the development board. This is due to the peripherals and IP that must be enabled 
in the FPGA to engage with the Ethernet PHYs. Also note that the total power consumption 
of the Ethernet FMC and development board is dependent on the ambient temperature and channel 
utilization.

Thermal Information
===================

We have not performed comprehensive thermal testing on the Ethernet FMC, however we recommend
that it be operated under ambient temperatures between 0 and 70 degrees C. This advice is based
on the recommended ambient operating temperatures of the critical devices on the Ethernet FMC.
These temperatures are listed in the table below.

+---------------------+------------------+------------+-----------+--------+
|                     | DEVICE           | MIN        | MAX       | UNIT   |
+=====================+==================+============+===========+========+
| | Ethernet FMC      | Ethernet PHY     | 0          | 70        |   C    |
| | Component         +------------------+------------+-----------+--------+
| | Ambient Operating | 25MHz Crystal    | -10        | 70        |   C    |
| | Temperatures      +------------------+------------+-----------+--------+
|                     | EEPROM           | -40        | 85        |   C    |
|                     +------------------+------------+-----------+--------+
|                     | MOSFET (FDV303N) | -55        | 150       |   C    |
|                     +------------------+------------+-----------+--------+
|                     | 125MHz LVDS      | -20        | 70        |   C    |
|                     | Clock Oscillator |            |           |        |
|                     +------------------+------------+-----------+--------+
|                     | RJ45 Connector   | 0          | 70        |   C    |
|                     | (JG0-0025NL)     |            |           |        |
|                     +------------------+------------+-----------+--------+
|                     | RJ45 Connector   | 0          | 70        |   C    |
|                     | (LPJG48851AFNL)  |            |           |        |
+---------------------+------------------+------------+-----------+--------+
| | Robust Ethernet   | Ethernet PHY     | 0          | 70        |   C    |
| | FMC Component     +------------------+------------+-----------+--------+
| | Ambient Operating | 25MHz Crystal    | -10        | 70        |   C    |
| | Temperatures      +------------------+------------+-----------+--------+
|                     | EEPROM           | -40        | 85        |   C    |
|                     +------------------+------------+-----------+--------+
|                     | MOSFET (FDV303N) | -55        | 150       |   C    |
|                     +------------------+------------+-----------+--------+
|                     | 125MHz LVDS      | -20        | 70        |   C    |
|                     | Clock Oscillator |            |           |        |
|                     +------------------+------------+-----------+--------+
|                     | Ethernet         | -40        | 85        |   C    |
|                     | Magnetics        |            |           |        |
|                     | (HX5020FNL)      |            |           |        |
|                     +------------------+------------+-----------+--------+
|                     | Ethernet         | -40        | 85        |   C    |
|                     | Magnetics        |            |           |        |
|                     | (LP5020NLR)      |            |           |        |
|                     +------------------+------------+-----------+--------+
|                     | RJ45 Connector   | -40        | 85        |   C    |
|                     | (RJE72-488-1411) |            |           |        |
+---------------------+------------------+------------+-----------+--------+

Components that are not listed in the table above (such as resistors, capacitors) are selected 
to have minimum operating temperature that is lower than 0 degrees C, and maximum operating
temperature that is greater than 70 degrees C.

Reset Timing
============

When hardware resetting the PHYs, we recommend using this timing:

#. Hold the RESET_N signal LOW for 10ms
#. Release the RESET_N signal (HIGH) and wait for 5ms


I2C (EEPROM) Timing
===================

The serial EEPROM (part number M24C02-FDW6TP) has a maximum operating clock frequency of 400 kHz.


MDIO Timing
===========

* The maximum MDC frequency supported by the 88E151x PHY is 12MHz.

88E151x Electrical and Timing
=============================

For electrical specs and timing related to the 88E151x signals listed below, please
refer to the `88E151x datasheet <https://www.marvell.com/content/dam/marvell/en/public-collateral/transceivers/marvell-phys-transceivers-alaska-88e151x-datasheet-2018-02.pdf>`_:

* Reset
* RGMII
* MDIO

Certifications
==============

* RoHS
* CE
