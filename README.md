#	`tiny486`
A reference board for OS/1337 on i486 developent

---

##	Why?
###	Lack of parts
Using old & used components to target `i486` is not a viable option, and getting reproduceable setups this way is not a feasible option long-term, as parts dry up.
- Fortunately, there are SBCs and SOMs using [Vortex86](https://en.wikipedia.org/wiki/Vortex86#Vortex86SX) Chips [which](https://www.vortex86.com/compare) are [i486SX](https://en.wikipedia.org/wiki/I486SX) & [i486DX](https://en.wikipedia.org/wiki/I486) compatibles.

### Standardization
####  Platform to target
Targeting a modern i486 implementation makes it easy to test and debug issues.

This includes:
- Having as much modularity as possible for integration
- Utilizing commercial off-the-shelf parts and still new made ones wherever possible.
  - Adapting old interfaces where doing so is a major quality-of-life improvement.
    - [USB instead of PS/2](https://www.youtube.com/watch?v=44tg6oXGmYI) [(HIDman)](https://github.com/rasteri/HIDman)
      - Allow the use of new, COTS parts (Keyboard & Mice).
        - For maximum compatibility a *"stupid"* set like the [Logitech MK120](https://www.logitech.com/en-us/shop/p/mk120-usb-keyboard-mouse) [[K120 Keyboard](https://www.logitech.com/en-us/shop/p/k120-usb-standard-computer.920-002478) + [M100 Mouse](https://www.logitech.com/en-us/shop/p/m100-usb-mouse.910-001601)] would be fine.
    - SATA instead of IDE (with [JM20330](documentation/external/JM20330.pdf) Host Bridge Chip[s] as [they seem to be the most reliable and stable](https://www.youtube.com/watch?v=oXShc_hDuqQ&t=1373s)).
      - [Alternatively](https://www.jmicron.com/products/list/17) [JMH330](documentation/external/JMH330.pdf) (IDE Master) + [JMH330S](documentation/external/JMH330S.pdf) (IDE Slave) for PATA -> SATA conversion.
      - Allow the use of new SSDs and ODDs and avoid expensive / low production number parts like some IDE-[Disk-on-Modules](https://en.wikipedia.org/wiki/Solid-state_drive#DOM).
  - Avoiding EoL & discontinued parts as much as possible!
    - Enshuring long-term availability (and reproduceability!)

### Archival / Bridging System
To allow access to older media, like Floppy Disks and legacy drives, a system that can interface with said controllers is necessary.
- PCI -> ISA is finnicky and doesn't work with low-level tools running on FreeDOS, OS/2 and MS-DOS.
  - Basically all ISA Bridge Chips seem to require some driver to be loaded at the host OS.
- [LPC -> ISA](https://github.com/rasteri/dISAppointment) support is [very dependent on the Mainboard used](https://www.youtube.com/watch?v=putHMSzu5og) and already on it's way out.

###	Expandable
####  Legacy Interfaces
Having actual expansion is the core benefit of using this over SBC-like setups that work great as applianced solutions but don't provide much in terms of development.
- ISA & PCI are the go-to internal expansion ports
- 2x RS-232 (DB-9) & 1x IEEE-1284 (Parallel) are the most used ones.

####	Modern Interfaces
Using older ISAs should not preclude modern interfaces and quality of life additions.
This includes:
- USB 2.0
  - SBC integrated controller
  - Optional: external controllers (PCI/ISA)
- Ethernet
  - SBC integrated controller
  - Optional external controllers (PCI/ISA)
- modern storage options
  - (micro)SD
    - Very convenient when it comes to small amounts of data.
    - Works fine in Low-IOPS / Low write cycle setups.
  - SATA
    - 2 Ports (from a single IDE Port, to allow both an ODD and SSD to be connected to it. [2x JM20330 chips](documentation/external/JM20330.pdf) or [JMH330](documentation/external/JMH330.pdf) + [JMH330S](documentation/external/JMH330S.pdf))

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
  - Allowing for both a useable ISA & PCI slot each.
    - ISA for legacy devices like FDD controllers.
    - PCI for additional medium speed devices.
  - No need to to decide for either/or.
  - Can be expanded to ATX with a passive backplane & extension cable is desired.

####  Flexible use-cases
Besides the main goal [being the hardware devkit for OS/1337], this board can also be used for various other use cases.
- Low-Cost Legacy Computing Basis
  - For those that need more power than a NuXT can provide.
  - Bridge System
    - Retro Gaming
    - Industrial Systems

---

##  Acknowledgements
Several projects and products deserve some recognition here.
### These are [listed here](documentation/acknowledgements.tsv)
####  Spechal Thanks go out to:
- [Andy "rasteri"](https://github.com/rasteri/) for the [Wee86](https://www.youtube.com/watch?v=ZBsv-jRiIT8) & [WeeCee](https://www.youtube.com/watch?v=aJEp4ZUG7BI) [project](https://github.com/rasteri/weeCee) as well as [HIDman](https://www.youtube.com/watch?v=44tg6oXGmYI) Adaptor for [PS/2](https://github.com/rasteri/HIDman)
- [Ian "polpo" Scott](https://github.com/polpo/) for the [PicoGUS](https://github.com/polpo/picogus)
- [Sergey Kiselev](https://github.com/skiselev/) for his extremely helpful work and designs for old 8/16-bit, ISA-based systems.


