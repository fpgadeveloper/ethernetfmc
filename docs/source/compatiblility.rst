.. _compatible-boards:

=================
Compatible Boards
=================

This section of the documentation aims to list all of the development boards for which compatibility
with the Ethernet FMC has been checked, and to list constraints and any notes concerning special 
requirements or limitations with the board.

List of boards
==============

The following development boards have been verified compatible with the Ethernet FMC. For more detailed
information regarding compatibility with a particular development board, including the availability
of an example design, click on the name of the board in the table below.

+---------------------------------------+----------------------------+-----------------------+
| Development board                     | Compatible with            | Compatible P/Ns       |
+=======================================+============================+=======================+
| :ref:`zedboard-notes`                 | | Ethernet FMC 2.5V        | | OP031-2V5           |
|                                       | | Robust Ethernet FMC 2.5V | | OP041-2V5           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`ac701-notes`                    | | Ethernet FMC 2.5V        | | OP031-2V5           |
|                                       | | Robust Ethernet FMC 2.5V | | OP041-2V5           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`kc705-notes`                    | | Ethernet FMC 2.5V        | | OP031-2V5           |
|                                       | | Robust Ethernet FMC 2.5V | | OP041-2V5           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`vc707-notes`                    | | Ethernet FMC 1.8V        | | OP031-1V8           |
|                                       | | Robust Ethernet FMC 1.8V | | OP041-1V8           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`vc709-notes`                    | | Ethernet FMC 1.8V        | | OP031-1V8           |
|                                       | | Robust Ethernet FMC 1.8V | | OP041-1V8           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`zc702-notes`                    | | Ethernet FMC 2.5V        | | OP031-2V5           |
|                                       | | Robust Ethernet FMC 2.5V | | OP041-2V5           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`zc706-notes`                    | | Ethernet FMC 2.5V        | | OP031-2V5           |
|                                       | | Robust Ethernet FMC 2.5V | | OP041-2V5           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`picozed-fmc-carrier-v2-notes`   | | Robust Ethernet FMC 1.8V | | OP041-1V8           |
|                                       | | Robust Ethernet FMC 2.5V | | OP041-2V5           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`microzed-fmc-carrier-notes`     | | Robust Ethernet FMC 2.5V | | OP041-2V5           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`ml605-notes`                    | | Ethernet FMC 2.5V        | | OP031-2V5           |
|                                       | | Robust Ethernet FMC 2.5V | | OP041-2V5           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`kcu105-notes`                   | | Ethernet FMC 1.8V        | | OP031-1V8           |
|                                       | | Robust Ethernet FMC 1.8V | | OP041-1V8           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`zcu102-rev-d-notes`             | | Ethernet FMC 1.8V        | | OP031-1V8           |
|                                       | | Robust Ethernet FMC 1.8V | | OP041-1V8           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`zcu102-notes`                   | | Ethernet FMC 1.8V        | | OP031-1V8           |
|                                       | | Robust Ethernet FMC 1.8V | | OP041-1V8           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`zcu104-notes`                   | | Ethernet FMC 1.8V        | | OP031-1V8           |
|                                       | | Robust Ethernet FMC 1.8V | | OP041-1V8           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`zcu106-notes`                   | | Ethernet FMC 1.8V        | | OP031-1V8           |
|                                       | | Robust Ethernet FMC 1.8V | | OP041-1V8           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`vcu108-notes`                   | | Ethernet FMC 1.8V        | | OP031-1V8           |
|                                       | | Robust Ethernet FMC 1.8V | | OP041-1V8           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`vcu118-notes`                   | | Ethernet FMC 1.8V        | | OP031-1V8           |
|                                       | | Robust Ethernet FMC 1.8V | | OP041-1V8           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`arria-10-attila-notes`          | | Robust Ethernet FMC 1.8V | | OP041-1V8           |
+---------------------------------------+----------------------------+-----------------------+
| :ref:`tebf0808-notes`                 | | Robust Ethernet FMC 1.8V | | OP041-1V8           |
+---------------------------------------+----------------------------+-----------------------+


Compatibility requirements
==========================

If you need to determine the compatibility of a development board that is not listed here, or you are designing
a carrier board to mate with the Ethernet FMC, please check your board against the list of requirements below.

VADJ
----
The development board must have the ability to supply a VADJ voltage of either 1.8VDC or 2.5VDC. The Ethernet
FMC has an EEPROM containing IPMI data to be used by a power management device. If the development board has
such a power management device, the correct VADJ will be applied automatically on power-up. Note that some
development boards require the VADJ voltage to be configured by a DIP switch or jumper placement.

Port 0
------
* FMC pins LA00, LA02, LA03, LA04, LA05, LA06, LA07, LA08 must be connected to the FPGA
* All of the above pins must be connected to the same I/O bank
* Ideally, LA00 should be routed to a clock capable pin

Port 1
------
* FMC pins LA01, LA06, LA09, LA10, LA11, LA12, LA13, LA14, LA15, LA16 must be connected to the FPGA
* All of the above pins must be connected to the same I/O bank
* Ideally, LA01 should be routed to a clock capable pin

Port 2
------
* FMC pins LA17, LA19, LA20, LA21, LA22, LA23, LA24, LA25 must be connected to the FPGA
* All of the above pins must be connected to the same I/O bank
* Ideally, LA17 should be routed to a clock capable pin

Port 3
------
* FMC pins LA18, LA26, LA27, LA28, LA29, LA30, LA31, LA32 must be connected to the FPGA
* All of the above pins must be connected to the same I/O bank
* Ideally, LA18 should be routed to a clock capable pin

If any of LA00, LA01, LA17 or LA18 are not connected to a clock capable pin, you may experience difficulty
achieving timing closure in your FPGA design. In some cases, timing closure can be still be achieved using 
non-clock capable pins by using carefully designed timing constraints.


.. _zedboard-notes:

ZedBoard
========

Mates with
----------

* `Ethernet FMC 2.5V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ (see note [#f1]_)
* `Robust Ethernet FMC 2.5V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ (see note [#f1]_)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth>`_
* `Zynq GEM based design <https://github.com/fpgadeveloper/ethernet-fmc-zynq-gem>`_

Connectors
----------

* **LPC**: Satisfies all of the Ethernet FMC requirements.

Setting VADJ
------------

The VADJ setting on this development board is determined by a pin header labelled J18. It should be set
to 1.8V or 2.5V depending on the voltage specification of the Ethernet FMC being used.


.. _ac701-notes:

AC701
=====

Mates with
----------

* `Ethernet FMC 2.5V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ (see note [#f1]_)
* `Robust Ethernet FMC 2.5V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ (see note [#f1]_)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth>`_

Connectors
----------

* **HPC**: Satisfies all of the Ethernet FMC requirements.

.. _kc705-notes:

KC705
=====

Mates with
----------

* `Ethernet FMC 2.5V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ (see note [#f1]_)
* `Robust Ethernet FMC 2.5V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ (see note [#f1]_)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth>`_

Connectors
----------

* **LPC**: Satisfies all of the Ethernet FMC requirements.
* **HPC**: Satisfies all of the Ethernet FMC requirements.

.. _vc707-notes:

VC707
=====

Mates with
----------

* `Ethernet FMC 1.8V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)
* `Robust Ethernet FMC 1.8V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth>`_

Connectors
----------

* **HPC1**: Satisfies all of the Ethernet FMC requirements.
* **HPC2**: Satisfies all of the Ethernet FMC requirements.

.. _vc709-notes:

VC709
=====

Mates with
----------

* `Ethernet FMC 1.8V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)
* `Robust Ethernet FMC 1.8V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth>`_

Connectors
----------

* **HPC**: Satisfies all of the Ethernet FMC requirements.

.. _zc702-notes:

ZC702
=====

Mates with
----------

* `Ethernet FMC 2.5V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ (see note [#f1]_)
* `Robust Ethernet FMC 2.5V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ (see note [#f1]_)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth>`_
* `Zynq GEM based design <https://github.com/fpgadeveloper/ethernet-fmc-zynq-gem>`_

Connectors
----------

* **LPC1**: Satisfies all of the Ethernet FMC requirements.
* **LPC2**: Satisfies all of the Ethernet FMC requirements.

.. _zc706-notes:

ZC706
=====

Mates with
----------

* `Ethernet FMC 2.5V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ (see note [#f1]_)
* `Robust Ethernet FMC 2.5V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ (see note [#f1]_)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth>`_
* `Zynq GEM based design <https://github.com/fpgadeveloper/ethernet-fmc-zynq-gem>`_

Connectors
----------

* **LPC**: Satisfies all of the Ethernet FMC requirements.
* **HPC**: Pins LA18_CC and LA17_CC of the HPC connector are routed to non-clock-capable pins so they cannot 
  properly receive the RGMII receive clocks for ports 2 and 3 of the Ethernet FMC. However this connector satisfies
  all of the requirements for ports 0 and 1 (note however that there is no example design for this connector
  at this time).

.. _picozed-fmc-carrier-v2-notes:

PicoZed FMC Carrier Card V2
===========================

Mates with
----------

* `Robust Ethernet FMC 2.5V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ 
  (when using the PicoZed SoM 7020) (see note [#f1]_)
* `Robust Ethernet FMC 1.8V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ 
  (when using the PicoZed SoM 7015 or 7030)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth>`_
* `Zynq GEM based design <https://github.com/fpgadeveloper/ethernet-fmc-zynq-gem>`_

Connectors
----------

* **LPC**: Satisfies all of the Ethernet FMC requirements.

.. _microzed-fmc-carrier-notes:

MicroZed FMC Carrier
====================

Mates with
----------

* `Robust Ethernet FMC 2.5V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ (see note [#f1]_)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth>`_ (for MicroZed 7020 only)
* `Zynq GEM based design <https://github.com/fpgadeveloper/ethernet-fmc-zynq-gem>`_

Connectors
----------

* **LPC**: Satisfies all of the Ethernet FMC requirements.

.. _ml605-notes:

ML605
=====

Mates with
----------

* `Ethernet FMC 2.5V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ (see note [#f3]_)
* `Robust Ethernet FMC 2.5V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=2.5V>`_ (see note [#f3]_)

Example designs
---------------

No example designs are currently available for this development board.

Connectors
----------

* **LPC**: Satisfies all of the Ethernet FMC requirements.
* **HPC**: Satisfies all of the Ethernet FMC requirements.


.. _kcu105-notes:

KCU105
======

Mates with
----------

* `Ethernet FMC 1.8V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)
* `Robust Ethernet FMC 1.8V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth>`_

Connectors
----------

* **LPC**: Satisfies all of the Ethernet FMC requirements.
* **HPC**: Satisfies all of the Ethernet FMC requirements.

.. _zcu102-rev-d-notes:

ZCU102 Rev-D
============

Mates with
----------

* `Ethernet FMC 1.8V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)
* `Robust Ethernet FMC 1.8V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth/tree/982ed68e779a88edb419eaa7ebef2221a77a4926>`_ 
  (only for version 2016.4)
* `ZynqMP GEM based design <https://github.com/fpgadeveloper/ethernet-fmc-zynq-gem/tree/a041ff5146a60e9d2caa95e61ce85d8acb885d76>`_
  (only for version 2016.4)

Connectors
----------

* **HPC0**: Satisfies all of the Ethernet FMC requirements.
* **HPC1**: The I/O pins for port 2 are routed to separate I/O banks by this connector, making it unusable. The other
  ports however may be used.

.. _zcu102-notes:

ZCU102
======

Mates with
----------

* `Ethernet FMC 1.8V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)
* `Robust Ethernet FMC 1.8V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth>`_
* `ZynqMP GEM based design <https://github.com/fpgadeveloper/ethernet-fmc-zynq-gem>`_

Connectors
----------

* **HPC0**: Satisfies all of the Ethernet FMC requirements.
* **HPC1**: The I/O pins for port 2 are routed to separate I/O banks by this connector, making it unusable. The other
  ports however may be used.

.. _zcu104-notes:

ZCU104
======

Mates with
----------

* `Ethernet FMC 1.8V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)
* `Robust Ethernet FMC 1.8V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)

Example designs
---------------

* `ZynqMP GEM based design <https://github.com/fpgadeveloper/ethernet-fmc-zynq-gem>`_

Connectors
----------

* **LPC**: Satisfies all of the Ethernet FMC requirements.

.. _zcu106-notes:

ZCU106
======

Mates with
----------

* `Ethernet FMC 1.8V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)
* `Robust Ethernet FMC 1.8V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)

Example designs
---------------

* `ZynqMP GEM based design <https://github.com/fpgadeveloper/ethernet-fmc-zynq-gem>`_

Connectors
----------

* **HPC0**: Satisfies all of the Ethernet FMC requirements.
* **HPC1**: This connector only has LA00-LA16 pins connected to the FPGA, therefore it can only support ports 0 and 1.

.. _vcu108-notes:

VCU108
======

Mates with
----------

* `Ethernet FMC 1.8V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)
* `Robust Ethernet FMC 1.8V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth/tree/9ba57cbffa3a55026fbf4855c8f9d1a746369ed5>`_ 
  (currently only available for version 2018.2 and for the HPC0 connector)

Connectors
----------

* **HPC0**: Satisfies all of the Ethernet FMC requirements.
* **HPC1**: Satisfies all of the Ethernet FMC requirements.

.. _vcu110-notes:

VCU110
======

The Xilinx VCU110 cannot be used with any Ethernet FMC. The VCU110 board's FMC connectors are only partially 
routed to the FPGA. Many I/Os that are required by the Ethernet FMC are not connected on this board.

.. _vcu118-notes:

VCU118
======

Mates with
----------

* `Ethernet FMC 1.8V <https://opsero.com/product/ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)
* `Robust Ethernet FMC 1.8V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)

Example designs
---------------

* `AXI Ethernet based design <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth/tree/898cae123256e1c11487862a3bcfc142d4e91c5d>`_
  (currently only available for ES1 silicon, only for version 2017.2 and only for the HPC connector)

Connectors
----------

* **HPC**: Satisfies all of the Ethernet FMC requirements.
* **FMC+**: Satisfies all of the Ethernet FMC requirements.

.. _arria-10-attila-notes:

Arria 10 Attila
===============

Mates with
----------

* `Robust Ethernet FMC 1.8V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_

Example designs
---------------

No example designs are currently available for this development board. Please contact 
`REFLEX CES <https://www.reflexces.com/products/development-kits/arria-10-instant-devkit/attila>`_ for support with
this carrier.

Connectors
----------

* **HPC**: Satisfies all of the Ethernet FMC requirements.

.. _tebf0808-notes:

TEBF0808
========

Mates with
----------

* `Robust Ethernet FMC 1.8V <https://opsero.com/product/robust-ethernet-fmc/?attribute_supply-voltage-vadj=1.8V>`_ (see note [#f2]_)

Example designs
---------------

* `ZynqMP GEM based design <https://github.com/fpgadeveloper/ethernet-fmc-zynq-gem>`_

Configuration
-------------

DIP switch S5 must be properly configured for correct boot and VADJ voltage.
Use one of the following settings depending on your desired boot mode.

+------------------------------------------------------------------------+
| DIP Switch S5                                                          |
+-----+-----+-----+-----+------------------------------------------------+
| 1   | 2   | 3   | 4   | Boot mode                                      |
+=====+=====+=====+=====+================================================+
| ON  | ON  | x   | ON  | SD/microSD or flash if no SD detected          |
+-----+-----+-----+-----+------------------------------------------------+
| OFF | ON  | x   | ON  | eMMC                                           |
+-----+-----+-----+-----+------------------------------------------------+
| ON  | OFF | x   | ON  | PJTAG0                                         |
+-----+-----+-----+-----+------------------------------------------------+
| OFF | OFF | x   | ON  | Main JTAG                                      |
+-----+-----+-----+-----+------------------------------------------------+

#. S5-3: Don't care - is user defined (by CPLD)
#. S5-4: Must be ON for FMC_VADJ 1.8V (OFF sets FMC_VADJ to 1.2V which is not
   supported by Ethernet FMC)

General board notes
-------------------

* The TEBF0808 requires a modified FSBL to setup clocks on the board before the bitstream is
  loaded and the application/OS is launched. The modifications are included in the example
  design repository and they are also described on the `Trenz Wiki for the TE0808 StarterKit <https://wiki.trenz-electronic.de/display/PD/TE0808+StarterKit>`_.


Footnotes
=========

.. [#f1] We recommend using the 2.5V version on this board however it can support the 1.8V 
         version with limitation. The FMC connector on this development board connects
         to HR (high-range) I/Os on the FPGA. Although HR I/Os can support many different I/O standards at 1.8V and
         2.5V, when it comes to LVDS they only support the `LVDS_25` standard which is designed for 2.5V. LVDS is
         required to receive the Ethernet FMC's 125MHz clock. For this reason, we recommend using the 2.5V version
         Ethernet FMC with all development boards whose FMC connector is linked to HR I/Os.
         If you must use the 1.8V Ethernet FMC on one of these boards, do not use the 125MHz clock in your
         FPGA design and instead use a local clock source with sufficient precision for Gigabit Ethernet.
.. [#f2] The device on this development board only has HP (high-performance) I/Os that don’t 
         support 2.5V levels. This board can therefore only support the 1.8V version Ethernet FMC.
         because they only have HP (high-performance) I/Os that don’t support 2.5V levels.
.. [#f3] The ML605 has a fixed VADJ of 2.5V.


