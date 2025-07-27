#	PC Card
##	Standards Overview 
####	Detailed Overview of the PC Card Standard

##	Table of Contents
Volume 1, Overview and Glossary
Volume 2, Electrical Specification
Volume 3, Physical Specification
Volume 4, Metaformat Specification
Volume 5, Card Services Specification
Volume 6, Socket Services Specification
Volume 7, Media Storage Specification
Volume 8, PC Card ATA Specification
Volume 9, XIP Specification
Volume 10, Guidelines
Volume 11, PCMCIA Specific Extensions
Volume 12, JEIDA Specific Extensions
Volume 13, PC Card Host System Specification
divider

##	Volume 1, Overview And Glossary
The PC Card Standard defines a 68-pin interface between the peripheral card and the socket into which it gets inserted. It defines three standard PC Card form factors, called Type I, Type II and Type III. All PC Cards measure the same length and width, differing only in thickness. Smaller cards can fit in larger sockets.
In addition to electrical and physical specifications, the PC Card Standard defines a software architecture to provide "plug and play" capability across the widest range of products. This software is made up of Socket Services and Card Services. It is Card and Socket Services that allow for interoperability of PC Cards.

####	PCMCIA/PC Card Standard Release History
#####	June 1990 - PCMCIA Standard Release 1.0/JEIDA 4.0 
- Electrical and physical specifications for memory cards only 
- Metaformat, or CIS (Card Information Structure) 

#####	September 1991 - PCMCIA Standard Release 2.0/JEIDA 4.1
- I/O interface 
- Support for dual-voltage memory cards 
- Card environmental requirements and testing methods 
- Socket Services Specification 
- eXecute In Place Specification 

#####	November 1992 - PCMCIA Standard Release 2.01
- PC Card ATA 
- Type III Form Factor 
- Card Services Specification 
- Socket Services enhanced to accommodate Card Services 

#####	July 1993 - PCMCIA Standard Release 2.1/JEIDA 4.2
- Card and Socket Services greatly enhanced 
- Electrical and Physical Specifications enhanced 

#####	February 1995 - PC Card Standard, February 1995 Release, First Printing
- 32-bit bus mastering interface (CardBus)
- Low Voltage Operation (3.3 V)
- Industry standard power management interface (APM)
- Support for DMA (Direct Memory Access)
- Multiple Function Cards 
- Stricter Compatibility Requirements 

#####	March 1995 - March 1995 Update
Included with the First Printing as an errata.
- General editorial changes 

#####	May 1995 - PC Card Standard, Second Printing
Incorporated March 1995 Update, along with:
- Power-up/Power-down Timing Errata 

#####	November 1995 - PC Card Standard, Third Printing
Incorporated March 1995 and May 1995 Updates, along with:
- Custom Interfaces 
- Indirect CIS Addressing 

#####	May 1996 - May 1996 PC Card Standard Update
Distributed only as errata.
- Zoomed Video (ZV) Interface Specification 
- Flash Translation Layer (FTL) 

#####	March 1997 - PC Card Standard, March 1997 Release, First Printing
This latest release of the PC Card Standard provides a variety of compatibility and functionality features. 
- All of the Updates to the February 1995 release, including Custom Interfaces and the Zoomed Video (ZV) Port Custom Interface are now incorporated in this release.
- A new Thermal Ratings system allows cards and hosts to be rated for thermal output, providing an interface to warn users of a potentially damaging thermal condition.

The following features have also been added:
- Power Management 
- ISDN Function Extension Tuples 
- Security and Instrumentation Card Function ID Tuples 
- Physical Socket Naming 
- Hot Dock/Undock Software Support 
- Streamlined PC Card Software Configuration 

##	Volume 2, Card Electrical
The Electrical Specification describes the connector pinout, interface protocol, signaling environment, interface timings, programming model, and specifics of card insertion, removal, power up, and configuration. It specifies both the 16-bit PC Card and 32-bit CardBus interfaces. The pin assignments for 16-Bit PC Card and 32-Bit CardBus interfaces are given here.

+================================================================+
| Pin Assignments For The PC Card And Cardbus Interfaces         |
+---+-----------------+---------+-----+-----------------+--------+
|   |      16-Bit     | 32-bit |$|    |     16-Bit      | 32-bit |
|   +-----------------+        |$|    +--------+--------+        +
|Pin| Memory |I/O+Mem |CardBus |$| Pin| Memory |I/O+Mem |CardBus |
+===+========+========+========+$+====+========+========+========+
|1  |GND     |GND     |GND     |$| 35 |GND     |GND     |GND     |
|2  |D3      |D3      |CAD0    |$| 36 |CD1#    |CD1#    |CCD1#   |
|3  |D4      |D4      |CAD1    |$| 37 |D11     |D11     |CAD2    |
|4  |D5      |D5      |CAD3    |$| 38 |D12     |D12     |CAD4    |
|5  |D6      |D6      |CAD5    |$| 39 |D13     |D13     |CAD6    |
+---+--------+--------+------- |$| ---+--------+--------+--------+
|6  |D7      |D7      |CAD7    |$| 40 |D14     |D14     |RSRVD   |
|7  |CE1#    |CE1#    |CCBE0#  |$| 41 |D15     |D15     |CAD8    |
|8  |A10     |A10     |CAD9    |$| 42 |CE2#    |CE2#    |CAD10   |
|9  |OE#     |OE#     |CAD11   |$| 43 |VS1#    |VS1#    |CVS1    |
|10 |A11     |A11     |CAD12   |$| 44 |RSRVD   |IORD#   |CAD13   |
+---+--------+--------+------- |$| ---+--------+--------+--------+
|11 |A9      |A9      |CAD14   |$| 45 |RSRVD   |IOWR#   |CAD15   |
|12 |A8      |A8      |CCBE1#  |$| 46 |A17     |A17     |CAD16   |
|13 |A13     |A13     |CPAR    |$| 47 |A18     |A18     |RSRVD   |
|14 |A14     |A14     |CPERR#  |$| 48 |A19     |A19     |CBLOCK# |
|15 |WE#     |WE#     |CGNT#   |$| 49 |A20     |A20     |CSTOP#  |
+---+--------+--------+------- |$| ---+--------+--------+--------+
|16 |READY   |IREQ#   |CINT#   |$| 50 |A21     |A21     |CDEVSEL#|
|17 |Vcc     |Vcc     |Vcc     |$| 51 |Vcc     |Vcc     |Vcc     |
|18 |Vpp1    |Vpp1    |Vpp1    |$| 52 |Vpp2    |Vpp2    |Vpp2    |
|19 |A16     |A16     |CCLK    |$| 53 |A22     |A22     |CTRDY#  |
|20 |A15     |A15     |CIRDY#  |$| 54 |A23     |A23     |CFRAME# |
+---+--------+--------+------- |$| ---+--------+--------+--------+
|21 |A12     |A12     |CCBE2#  |$| 55 |A24     |A24     |CAD17   |
|22 |A7      |A7      |CAD18   |$| 56  A25     |A25     |CAD19   |
|23 |A6      |A6      |CAD20   |$| 57 |VS2#    |VS2#    |CVS2    |
|24 |A5      |A5      |CAD21   |$| 58 |RESET   |RESET   |CRST#   |
|25 |A4      |A4      |CAD22   |$| 59 |WAIT#   |WAIT#   |CSERR#  |
+---+--------+--------+------- |$| ---+--------+--------+--------+
|26 |A3      |A3      |CAD23   |$| 60 |RSRVD   |INPACK# |CREQ#   |
|27 |A2      |A2      |CAD24   |$| 61 |REG#    |REG#    |CCBE3#  |
|28 |A1      |A1      |CAD25   |$| 62 |BVD2    |SPKR#   |CAUDIO  |
|29 |A0      |A0      |CAD26   |$| 63 |BVD1    |STSCHG# |CSTSCHG |
|30 |D0      |D0      |CAD27   |$| 64 |D8      |D8      |CAD28   |
+---+--------+--------+------- |$| ---+--------+--------+--------+
|31 |D1      |D1      |CAD29   |$| 65 |D9      |D9      |CAD30   |
|32 |D2      |D2      |RSRVD   |$| 66 |D10     |D10     |CAD31   |
|33 |WP      |IOIS16# |CCLKRUN#|$| 67 |CD2#    |CD2#    |CCD2#   |
|34 |GND     |GND     |GND     |$| 68 |GND     |GND     |GND     |
+===+========+========+========+=+====+========+========+========+


##	Volume 3, Card Physical
This section defines physical outline dimensions, basic mechanical capabilities and environmental conditions under which PC Cards are expected to operate. Information is provided for Type I, II, and III PC Cards, for 5 volt and low voltage equivalents, and for the 32-bit CardBus interface.

+==========================================+
| PC Card Physical Characteristics         |
+====================+=====================+
| Physical Interface |  68 Pins            |
| Back End I/O Conn. |  Proprietary*       |
| Length             |  85.6 mm            |
| Width              |  54.0 mm            |
| Thickness          |  Type I = 3.3 mm    |
|                    |  Type II = 5.0 mm   |
|                    |  Type III = 10.5 mm |
| Operating Temp.    |  0 to 55 C          |
| Storage Temp.      |  -20 to 65 C        |
| Minimum Insertions |  Office Env. 10,000 |
|                    |  Harsh Env.  5,000  |
+====================+=====================+

- Two standardized connectors are available as part of the optional PCMCIA Specific Extensions Specifications.


##	Volume 4, Metaformat Specification
The goal of the Metaformat Specification is to allow PC Cards to handle numerous, somewhat incompatible data-recording formats and data organizations. Metaformat is also known as Card Information Structure (CIS). As is done with networking standards, the Metaformat is a hierarchy of layers. Below the Metaformat is the physical layer, the electrical and physical interface characteristics of PC Cards. The Metaformat layers are Basic Compatibility, Data Recording, Data Organization, and System-Specific.
- The Basic Compatibility Layer - specifies a minimal level of card-data organization. Tuples at this level provide fundamental information about the PC Cards including supported configurations, manufacturer, and individual device characteristics such as size, speed, and programming information. An example of a tuple from the Basic Compatibility Layer is the Function ID Tuple, shown here.

+====================================================+
| CISTPL_FUNCID: Function Identification Tuple       |
+--+---------+--+--+---------+
|Code| Name             |    |Code| Name             |
+====+==================+====+====+==================+
| 0  | Multi-Function   |    | 7  | AIMS             |
+----+------------------+    +----+------------------+
| 1  | Memory           |    | 8  | SCSI             |
+----+------------------+    +----+------------------+
| 2  | Serial Port      |    | 9  | Security         |
+----+------------------+    +----+------------------+
| 3  | Parallel Port    |    |A-FD| Reserved         |
+----+------------------+    +----+------------------+
| 4  | Fixed Disk       |    | FE | Vendor-Specific  |
+----+------------------+    +----+------------------+
| 5  | Video Adapter    |    | FF | Do Not Use       |
+----+------------------+    +----+------------------+
| 6  | Network Adapter  |    |    |                  |
+====+==================+====+====+==================+

#####	The Data Recording Layer 
- includes tuples which describe partitioning information and provide card initialization information.

#####	The Data Organization Layer 
- currently includes a single tuple, CISTPL_ORG, which specifies the partition organization (for example, the file system) in use in a partition described by Data Recording Format Layer tuple(s).

#####	The System-Specific Layer 
- includes the special purpose tuple, CISTPL_SPCL, and the range of vendor-unique tuple codes. The special purpose tuple provides a mechanism for documenting the format and interpretation of special tuple usage within the PC Card Standard. the format and interpretation of special tuple usage within the PC Card Standard. The format and interpretation of any tuple inthe vendor-unique range is not documented within the Standard.

##	Volume 5, Card Services
Card Services describes an API (Application Programming Interface) which allows PC Cards and sockets to be shared by multiple clients. Clients are the programs that access Card Servicse and may be devices drivers, configuration utilities or application programs. This specification is intended to be independent of the hardware that actually manipulates PC Cards and sockets.
Card Services has two goals. First to support the ability of PC Card-aware devices drivers, configuration utilities and application programs to share PC Cards, sockets and system resources. Second is to provide a centralized resource for the common functionality required by these clients.
Card Services is structured in a client/server model. Application programs, device drivers and utility programs are the clients requesting services. Card Services is the server providing the services requested by clients. the Card Services interface defines how the clients and servers communicate.
back to top of page


##	Volume 6, Socket Services
Socket Services is the lowest layer in a multi-layer architecture that manages resources on PC Cards. Socket Services provides a universal software interface to the hardware that controls sockets for PC Cards. It masks the details of the hardware used to implement these sockets, allowing higher-level software to be developed which is able to control and utilize PC Cards without any knowledge of the actual hardware interface. Software layers above Socket Services provide additional capabilities. Immediately above Socket Services is Card Services.
Socket Services approaches the handling it manages by addressing it as a number of objects with different areas of functionality. Adapters are the hardware that connects a host system's bus to PC Card sockets. Sockets are receptacles for PC Cards. Host systems may have more than one adapter, and each adapter may have one or more sockets.
Socket Services reports the number of sockets, windows and EDC generators provided by each adapter installed. Adapter power consumption and stats change reporting may be controlled separately for each adapter. Socket Services describes the characteristics of each socket and allows socket resources to be manipulated and current settings determined.
back to top of page

##	Volume 7, Media Storage Formats
The Media Storage Formats Specification describes how data are formatted on PC Cards used as storage devices, primarily Flash storage devices, to promote the exchange of these cards among different host systems. The included formats are:
- MS-DOS BPB/FAT Format
- Linear File Store
- Flash Translation Layer 

##	Volume 8, PC Card ATA
The PC Card ATA Standard describes the operation of mass storage PC Cards using the protocol of the ANSI AT Attachment (ATA) Interface for Disk Drives in the PC Card environment. This standard includes both the usage of the ANSI ATA-defined protocols and the differences required due to conflicts between the PC Card and ANSI ATA Standards.

##	Volume 9, eXecute In Place (Xip)
XIP outlines a method of directly executing applications from ROM without loading the image of the application into RAM prior to execution. The XIP specification describes the Metaformat tuples, data structures, driver architecture, and API for XIP, as well as the architecture and load format of XIP-compliant applications.
back to top of page

##	Volume 10, Guidelines
Guidelines is designed to provide implementation examples and further explanations of the PC Card Standard in order to:
- Enhance the interoperability of PC Card components, including systems and cards hardware and software, and applications. 
- Facilitate the development of PC Card hardware and software by increasing the understanding of the standard by developers. 

These guidelines are not requirements made by the PCMCIA/JEIDA standards organizations. Rather they are implementation examples, suggestions and hints. The following guidelines are included:
- Enabler Capabilities and Bahavior 
- Card-Application Behavior 
- Fax/Modem Card Information Structure Design 
- Wireless Card Information Structure Design 
- Sample PC Card ATA Tuple Options 
- CardBus/PCI Common Silicon Requirements 
- CardBus Operational Scenarios 
- Guidelines for CIS Tuples for 3.3 or 3.3/5 volt Operation 

##	Volume 11, PCMCIA Specific Extensions
There are two volumes within the PC Card Standard that are not universally applied. When the two standards organizations, JEIDA and PCMCIA, investigated the large amount of commonality between their respective specifications, a standard PC Card specification resulted. However, additional needs were defined by the individual standards groups, and a set of group-specific extensions was proposed. These extensions allow each organization to provide specifications unique to its respective clientele, while maintaining all other features under a common standard release. These extensions are not mutually exclusive and can both be added to a system or card.

- The Auto-Indexing Mass Storage (AIMS) section describes a standard for storing large data sets, such as image and multimedia data files. Block-oriented mass storage devices are supported by this extension.
- 15-pin Shielded Modem I/O connector - describes the physical characteristics of a recommended connector for LAN and Modem I/O devices.
- 7-pin Modem I/O connector - describes connectors suitable for use and an external I/O interface from PC Cards used for modem and Fax applications.
- The Recommended Extensions section provides physical specifications for Type III, and Type I and II Extended form factors.

##	Volume 12, JEIDA Specific Extensions
- Small Block Flash Format - a file format for flash memory cards in which the memory devices are EEPROMs. The concept is to make the filessystems simple to operate and of compact size.
- SISRIF (Still Image, Sound and Related Information Format for PC Card DSC 68-Pin Standards - the purpose is to stipulate the methods for recording image and audio data on PC Cards.
- DRAM Card Specifications - sets the standard for an 88-pin DRAM PC Card for expanding memory for personal computers using hyper page mode (EDO) dynamic random access memory (DRAM).

##	Volume 13, PC Card Host System Specification
This newest Volume of the PC Card Standard currently defines the Host Side portion of the new Thermal Ratings Specification, which gives a maximum thermal capacity for host systems. As new specifications are developed in the PCMCIA committee for PC Card hosts, they will be placed in this Volume.
