===============
Getting Started
===============

Example Designs
===============

The example designs for the Ethernet FMC are hosted on `Github`_. There are currently
four designs, hosted in separate repositories. Each example design supports multiple
development boards and they all work with the Ethernet FMC and Robust Ethernet FMC 
interchangeably.

+-----------------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
| AXI Ethernet design         | `Source code <https://github.com/fpgadeveloper/ethernet-fmc-axi-eth>`__       | `Docs <https://axieth.ethernetfmc.com/>`__                                     |
+-----------------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
| PS GEM design               | `Source code <https://github.com/fpgadeveloper/ethernet-fmc-zynq-gem>`__      | `Docs <https://zynqgem.ethernetfmc.com/>`__                                    |
+-----------------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
| Maximum throughput design   | `Source code <https://github.com/fpgadeveloper/ethernet-fmc-max-throughput>`__| `Docs <https://github.com/fpgadeveloper/ethernet-fmc-max-throughput#readme>`__ |
+-----------------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------+
| Processorless design        | `Source code <https://github.com/fpgadeveloper/ethernet-fmc-processorless>`__ | `Docs <https://github.com/fpgadeveloper/ethernet-fmc-processorless#readme>`__  |
+-----------------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------+

AXI Ethernet based example
--------------------------

This example design is based on Xilinx's soft (ie. FPGA implemented) MAC,
the `AXI Ethernet Subsystem IP`_, that can be found in the Vivado IP Catalog.
As the MAC is implemented in the FPGA fabric, this example is ideal for pure
FPGA designs or Zynq/ZynqMP designs that require some packet processing to be 
performed in the FPGA.

PS GEM based example
--------------------

This example design utilizes the Gigabit Ethernet MACs (GEMs) that are embedded
into the Processing System (PS) of the Zynq 7000™ and Zynq Ultrascale+™ devices.
The MACs in this example design do not use up any of the FPGA fabric, which
makes it ideal for applications that need to use the FPGA for other purposes.

Maximum throughput example
--------------------------

This example design demonstrates the use of an FPGA based packet generator
designed in HLS to achieve raw data transmission over the Ethernet ports at the
maximum throughput.

Processorless example
---------------------

This example demonstrates how the Ethernet FMC can be used without a processor.
All of the packet generation and processing is done entirely by state
machines in the FPGA fabric. The design also contains the logic for bringing
up the PHYs and configuring the TEMAC.

.. _Github: https://github.com
.. _AXI Ethernet Subsystem IP: https://www.xilinx.com/products/intellectual-property/axi_ethernet.html
