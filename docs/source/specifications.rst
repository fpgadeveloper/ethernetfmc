==============
Specifications
==============

Recommended Operating Conditions
================================

+-------------------+------------------------+------------+------------+-----------+--------+
|                                            | MIN        | TYP        | MAX       | UNIT   |
+===================+========================+============+============+===========+========+
| Supply voltage    | 12 VDC                 |    +12     |    +12     |    +12    |    V   |
|                   +------------------------+------------+------------+-----------+--------+
|                   | 3.3 VDC                |    +3.3    |    +3.3    |    +3.3   |    V   |
|                   +------------------------+------------+------------+-----------+--------+
|                   | VADJ 2.5VDC            |    +2.5    |    +2.5    |    +2.5   |    V   |
|                   +------------------------+------------+------------+-----------+--------+
|                   | VADJ 1.8VDC            |    +1.8    |    +1.8    |    +1.8   |    V   |
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

Reset Timing
============

When hardware resetting the PHYs, we recommend using this timing:

#. Hold the RESET_N signal LOW for 10ms
#. Release the RESET_N signal (HIGH) and wait for 5ms


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
