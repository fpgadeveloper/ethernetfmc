=================
Programming Guide
=================

This section provides the details of the programming requirements to operate the Ethernet FMC
hardware and customise functionality.

PHY registers
=============

For correct operation of the Ethernet FMC, the 4x Marvell Gigabit Ethernet PHYs must be properly
configured over the MDIO bus (for more information, see :ref:`phy-config`). The Marvell PHYs have
registers that control the operation and functionality of the device and the Ethernet link. The
registers have default values that are applied when the PHY is powered up and released from reset.
The default register values are suitable for a wide range of use cases, but some of them you might
want to change to suit your application. 

The tables below list some of the registers and settings that are useful for basic operation of 
the Ethernet FMC. For a comprehensive list of the registers, please refer to the `public datasheet`_.

.. _Page 0, Register 0:

Copper Control Register, Page 0, Register 0
-------------------------------------------

+------------+---------------------------------+----------+----------------+
| Bits       | Description                     | Mode     | Default Value  |
+============+=================================+==========+================+
| 15         | Copper software reset           | R/W, SC  | 0x0            |
+------------+---------------------------------+----------+----------------+
| 12         | Enable Auto-negotiation         | R/W      | 0x1            |
+------------+---------------------------------+----------+----------------+
| 9          | Restart Auto-negotiation        | R/W, SC  | 0x0            |
+------------+---------------------------------+----------+----------------+

.. _Page 0, Register 1:

Copper Status Register, Page 0, Register 1
------------------------------------------

+------------+---------------------------------+----------+----------------+
| Bits       | Description                     | Mode     | Default Value  |
+============+=================================+==========+================+
| 5          | Auto-negotiation Complete       | RO       | 0x0            |
+------------+---------------------------------+----------+----------------+

.. _Page 0, Register 4:

Copper Auto-Negotiation Advertisement Register, Page 0, Register 4
------------------------------------------------------------------

+------------+---------------------------------+----------+----------------+
| Bits       | Description                     | Mode     | Default Value  |
+============+=================================+==========+================+
| 11         | Asymmetric pause                | R/W      | 0x0            |
+------------+---------------------------------+----------+----------------+
| 10         | MAC pause                       | R/W      | 0x0            |
+------------+---------------------------------+----------+----------------+
| 8          | Advertise 100Mbps full duplex   | R/W      | 0x1            |
+------------+---------------------------------+----------+----------------+
| 7          | Advertise 100Mbps half duplex   | R/W      | 0x1            |
+------------+---------------------------------+----------+----------------+
| 6          | Advertise 10Mbps full duplex    | R/W      | 0x1            |
+------------+---------------------------------+----------+----------------+
| 5          | Advertise 10Mbps half duplex    | R/W      | 0x1            |
+------------+---------------------------------+----------+----------------+

.. _Page 0, Register 9:

1000BASE-T Control Register, Page 0, Register 9
-----------------------------------------------

+------------+---------------------------------+----------+----------------+
| Bits       | Description                     | Mode     | Default Value  |
+============+=================================+==========+================+
| 9          | Advertise 1Gbps full duplex     | R/W      | 0x1            |
+------------+---------------------------------+----------+----------------+
| 8          | Advertise 1Gbps half duplex     | R/W      | 0x1            |
+------------+---------------------------------+----------+----------------+

.. _Page 0, Register 17:

Copper Specific Status Register 1, Page 0, Register 17
------------------------------------------------------

+------------+---------------------------------+----------+----------------+
| Bits       | Description                     | Mode     | Default Value  |
+============+=================================+==========+================+
| 15:14      | | Established link speed        | RO       | 0x2            |
|            | | Valid only when speed and     |          |                |
|            |   duplex resolved asserted      |          |                |
|            |   (bit 11)                      |          |                |
|            | | 10b = 1Gbps                   |          |                |
|            | | 01b = 100Mbps                 |          |                |
|            | | 00b = 10Mbps                  |          |                |
+------------+---------------------------------+----------+----------------+
| 11         | Speed and duplex resolved       | RO       | 0x0            |
+------------+---------------------------------+----------+----------------+

.. _Page 0, Register 19:

Copper Interrupt Status Register, Page 0, Register 19
-----------------------------------------------------

+------------+---------------------------------+----------+----------------+
| Bits       | Description                     | Mode     | Default Value  |
+============+=================================+==========+================+
| 15         | Auto-negotiation Error          | RO, LH   | 0x0            |
+------------+---------------------------------+----------+----------------+

.. _Any page, Register 22:

Page Address, Any page, Register 22
-----------------------------------

When accessing registers, we must set the page address register to the value of the page
that is being targetted. For example, when accessing the MAC Specific Control Reg 2
(page 2, register 21), we must first set the page address register (register 22) to
2 prior to performing the register access.

+------------+---------------------------------+----------+----------------+
| Bits       | Description                     | Mode     | Default Value  |
+============+=================================+==========+================+
| 7:0        | For changing the Page Address   | R/W      | 0x00           |
+------------+---------------------------------+----------+----------------+

.. _Page 2, Register 21:

MAC Specific Control Reg 2, Page 2, Register 21
-----------------------------------------------

+------------+--------------------------------------------------+----------+----------------+
| Bits       | Description                                      | Mode     | Default Value  |
+============+==================================================+==========+================+
| 5          | | RGMII Rx Timing Control                        | R/W      | 0x1            |
|            | | 1 = Rx clock transitions when data stable      |          |                |
|            | | 0 = Rx clock transitions when data transitions |          |                |
+------------+--------------------------------------------------+----------+----------------+
| 4          | | RGMII Tx Timing Control                        | R/W      | 0x1            |
|            | | 1 = Tx clock delay enabled in PHY              |          |                |
|            | | 0 = Tx clock delay disabled in PHY             |          |                |
+------------+--------------------------------------------------+----------+----------------+

Register modes
--------------

* R/W: Read and write
* RO: Read only
* SC: Self clearing
* LH: Latches high until read or reset occurs

Autonegotiation
---------------

After a hardware reset, the PHYs are configured by default to auto-negotiate with the link partner and advertise all possible link capabilities 
(1Gbps, 100Mbps, 10Mbps, full and half duplex). If desired, we can setup and initiate the auto-negotiation process manually through the PHY 
registers. One suggested method for doing this is illustrated by the following pseudocode:

#. Set :ref:`Any page, Register 22` to 0
#. Read value of :ref:`Page 0, Register 4`

   * Enable asymmetric pause (assert bit 11)
   * Enable MAC pause (assert bit 10)
   * Advertise 100Mbps, 10Mbps, full and half duplex (assert bits 8,7,6 and 5)
   
#. Write new value to :ref:`Page 0, Register 4`
#. Read value of :ref:`Page 0, Register 9`

   * Advertise 1Gbps full and half duplex (assert bits 9 and 8)
   
#. Write new value to :ref:`Page 0, Register 9`
#. Read value of :ref:`Page 0, Register 0`

   * Enable auto-negotiation (assert bit 12)
   * Restart auto-negotiation process (assert bit 9)
   
#. Write new value to :ref:`Page 0, Register 0`
#. Read value of :ref:`Page 0, Register 0`

   * Trigger software reset (assert bit 15)
   
#. Write new value to :ref:`Page 0, Register 0`
#. Check the value of :ref:`Page 0, Register 0` until software reset (bit 15) is deasserted
#. Read value of :ref:`Page 0, Register 1`
#. If auto-negotiation NOT complete (bit 5 deasserted) then

   * Wait for 1 second
   * Read value of :ref:`Page 0, Register 19`
   * If auto-negotiation error (bit 15), then abort the process
   * Read value of :ref:`Page 0, Register 1`
   * Repeat this process
  
#. Read value of :ref:`Page 0, Register 17` to determine link speed from bits 15:14

RGMII timing
------------

As described in `RGMII Interface Timing Considerations <http://ethernetfmc.com/rgmii-interface-timing-considerations/>`_, the RGMII
RX and TX clock skews must be appropriately configured in the PHY for proper operation of the Ethernet FMC. By default, both the RX
and TX clock skews are enabled in the PHY, however for most applications, the TX clock skew must be disabled. The following pseudocode
illustrates how to disable the TX clock skew, while leaving the RX clock skew enabled:

#. Set :ref:`Any page, Register 22` to 2
#. Read value of :ref:`Page 2, Register 21`

   * Disable TX clock delay (deassert bit 4)
   * Enable RX clock delay (assert bit 5)
   
#. Write new value to :ref:`Page 2, Register 21`


.. _public datasheet: https://www.marvell.com/content/dam/marvell/en/public-collateral/transceivers/marvell-phys-transceivers-alaska-88e151x-datasheet.pdf
