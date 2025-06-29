#	`tiny486`
A reference board for OS/1337 on i486 developent

---

##	Why?
###	Lack of parts
Using old & used components to target `i486` is not a viable option, and getting reproduceable setups this way is not a feasible option long-term, as parts dry up.
- Fortunately, there are SBCs and SOMs using [Vortex86](https://en.wikipedia.org/wiki/Vortex86#Vortex86SX) Chips [which](https://www.vortex86.com/compare) are [i486SX](https://en.wikipedia.org/wiki/I486SX) & [i486DX](https://en.wikipedia.org/wiki/I486) compatibles.

####	Standardized Platform to target
Targeting a modern i486 implementation makes it easy to test and debug issues.

### Archival / Bridging System
To allow access to older media, like Floppy Disks and legacy drives, a system that can interface with said controllers is necessary.
- PCI -> ISA is finnicky and doesn't work with low-level tools running on FreeDOS, OS/2 and MS-DOS.
  - LPC -> ISA support is very dependent on the Mainboard used and already on it's way out.

###	Expandable
Having actual expansion is the core benefit of using this over SBC-like setups that work great as applianced solutions but don't provide much in terms of development.

####	Modern Interfaces
Using older ISAs should not preclude modern interfaces and quality of life additions.
This includes:
- USB
- Ethernet
- modern storage options
  - (micro)SD
  - SATA

Said interfaces should be provided by the used SoM/SoC per it's own pin headers and merely "fanned out" with breakout cables.
- The mainboard itself doesn't carry them as to save costs.
  - OFC one can add them via PCI and/or ISA cards but that would tie up bandwith for these slots.

####	Legacy Interfaces
Having means to interface to legagy hardware using [ISA](https://en.wikipedia.org/wiki/Industry_Standard_Architecture) (and [PCI](https://en.wikipedia.org/wiki/Peripheral_Component_Interconnect)) is the whole point of the design.
- If legacy interfaces weren't required, there would be no need for hardware, and everything could be done in [QEMU](https://en.wikipedia.org/wiki/QEMU).
  - More modern Interfaces like [PCIe](https://en.wikipedia.org/wiki/PCI_Express) can be attained using PCI->PCIe chips like the [PEX 8112](https://docs.broadcom.com/doc/12351805) which can be bought on [off-the-shelf adaptor cards](https://www.kalea-informatique.com/pci-to-pci-express-x16-bridge-card-pex8112-chipset.htm) that are ready to use.

###	Flexible Mainboard option
Aiming to be a a flexible and useful board for said use-cases.
- Aiming at [Mini-DTX](https://en.wikipedia.org/wiki/DTX_(form_factor)) (but could be expanded to [Micro-ATX](https://en.wikipedia.org/wiki/MicroATX)  and [ATX](https://en.wikipedia.org/wiki/ATX))...

---

##  Acknowledgements
Several projects and products deserve some recognition here.
### These are [listed here](documentation/acknowledgements/others.tsv)
####  Spechal Thanks go out to:
- [Andy "rasteri"](https://github.com/rasteri/) for the Wee86 & WeeCee
- [Ian "polpo" Scott](https://github.com/polpo/) for the PicoGUS
- [Sergey Kiselev](https://github.com/skiselev/) for his extremely helpful work and designs for old 8/16-bit, ISA-based systems.


