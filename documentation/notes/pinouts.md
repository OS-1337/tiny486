# `tiny486`
###	Pinouts

##	[PCI](en.wikipedia.org/wiki/Peripheral_Component_Interconnect#Connector_pinout)
55x2 = 110 pins
- 62x2 contacts
   - 1x 2pins PCI-X 64-bit enable (not connected on 32 bit PCI slot!)
   - 26 pins ground 
     - 4x2 key notches (5V / 3,3V cutouts -> GND)
   - 24 pins power
     - 13x +3,3V
     - 9x +5V
     - 1x -12V
     - 1x +12V
   - 32x Adress/Data Lines
  - 5 signalling pinst from the card
    - 2x PRSNT# Pins to indicate power draw: either 7,5W; 15W or 25W
  - 5x IOPWR pins
    - either 5V or 3,3V
  - 9x Open-Drain Interrupt pins
  - 8x Board to Card pins for interrupts and control (clock, reset, bus enable)
  - 9x Initiator Output
  - 3x Target Output
  - 4x reserved pins (not to be connected!)
  - 4x C/BE# pins

##	[https://en.wikipedia.org/wiki/Industry_Standard_Architecture#ISA_bus_architecture]
49x2 = 98 pins
