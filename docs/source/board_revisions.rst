Board Revision History
======================

Ethernet FMC
------------

Rev 1-1
^^^^^^^

* Date of first manufacture: 2014-12-15
* First board release
* Supports VADJ 2.5V only

Rev B
^^^^^^^

* Date of first manufacture: 2015-03-27
* Increased via tenting diameters underneath QFNs to increase
  manufacturing yield
* Optimizations to bottom layer planes
* Added solder jumpers to REF_CLK_FSEL [#f1]_ and REF_CLK_OE [#f2]_ signals (see note [#f3]_).
* 125MHz oscillator VCC now connected to 3.3VDC

.. [#f1] REF_CLK_FSEL is an input of the clock oscillator and allows the output frequency
         to be set to either 125MHz or 250MHz. Floating this pin results in an
         output of 125MHz.

.. [#f2] REF_CLK_OE is the output enable input of the clock oscillator. Floating this pin
         results in output being enabled.

.. [#f3] These REF_CLK_FSEL and REF_CLK_OE jumpers are shorted on the 2.5V version to allow 
         the signals to be driven by the carrier board. These jumpers are left
         OPEN on the 1.8V version, as 1.8VDC is not sufficient to drive them. This effectively 
         floats the inputs and results in an always-enabled output of 125MHz.

Rev C
^^^^^^^

* Date of first manufacture: 2015-05-07
* Increased via tenting diameters underneath QFNs to increase
  manufacturing yield
* Removed "2V5" from silkscreen

Rev D
^^^^^^^

* Date of first manufacture: 2015-07-16
* R24, R25 changed to 240R 0402 to reduce part count
* Via tenting under QFNs replaced by via-in-pad

Rev E
^^^^^^^

* Date of first manufacture: 2016-05-02
* Changed 125MHz oscillator to Micrel MEMS part DSC1123CI2-125.0000
  to replace obsolete On Semi part NBXDPA019LNHTAG
* Removed FSEL option - consequence of the oscillator part change
* Added buffer to CLK_EN input to allow it to be driven at 1.8V
* Removed the solder jumpers for FSEL and CLK_EN
* Expanded FMC solder paste pads to improve manufacturing yield
* Changed chassis filter capacitor to 1kV in 0805 package

Rev F
^^^^^^^

* Date of first manufacture: 2020-02-04
* JG0-0025NL Quad RJ45 footprint optimized to facilitate assembly
* Added CE logo to silkscreen


Robust Ethernet FMC
-------------------

Rev A
^^^^^^^

* Date of first manufacture: 2015-06-10
* First board release
* RJ45 part Amphenol RJE72-488-1401 (no LEDs)
* Uses dual color LEDs Avago HSMF-C157
* 4-layer PCB design

Rev B
^^^^^

* Date of first manufacture: 2016-02-12
* Changed 125MHz oscillator to Micrel MEMS part DSC1121DI2-125.0000T
  to replace obsolete On Semi part NBXDPA019LNHTAG
  (device with CMOS outputs and 2.5mm x 2.0mm package)
* Removed FSEL option - consequence of the oscillator part change
* Added buffer to CLK_EN input to allow it to be driven at 1.8V
* Removed the solder jumpers for FSEL and CLK_EN
* RJ45 part changed to Amphenol RJE72-488-1451 (with LEDs)
* Removed Avago HSMF-C157 dual color LEDs

This revision was never released due to procurement difficulty of the
Micrel MEMS part. It was mistakenly designed for CMOS device 
DSC1121DI2-125.0000T which was available at the time, however in order
to satisfy the VITA 57.1 standard the device used should have had 
LVDS outputs. The Micrel part variant with LVDS outputs was not
procurable in the same package at that time, so we did not release
Rev-B and we incorporated the package and device change in Rev-C.

Rev C
^^^^^^^

* Date of first manufacture: 2016-05-05
* Changed 125MHz oscillator to Micrel MEMS part DSC1123CI2-125.0000
  (device with LVDS outputs and 3.2mm x 2.5mm package)

Rev D
^^^^^^^

* Date of first manufacture: 2017-06-22
* Redesigned PCB to 8-layers to internalize RGMII traces in an effort
  to reduce radiated emissions

Rev E
^^^^^^^

* Date of first manufacture: 2020-08-25
* PHY thermal vias now via-in-pad
* Changed R24 and R25 to 240R 0402 from 0603
* Added CE logo to silkscreen

