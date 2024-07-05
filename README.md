# Agnus_1MB_TTH
1 MB Agnus card for SMD2000 using TTH ram

## SMD 2000 1 MB TTH Agnus Card
This is the 1 MB TTH Agnus card for the SMD2000 "BUSHFIRE" project, a mini-DTX sized Amiga 2000.  
Official project information can be found at Amiga Retro Brisbane projects page:
https://www.amigaretro.com/projects/

This card is for constructors who wish to use a 1 MB or 512 kB Agnus from an Amiga 500 or Amiga 2000: 8370; 8371; 8372A; and certain 8375s, and wish to reuse the ram from the donor machine.  See below.
If you intend to use a 2 MB 8375 Agnus from an A500+ or A600 build the 2 MB card.

There are two other Agnus cards to choose from; a 1 MB card that uses SMD ram instead of TTH ram, and a 2 MB Agnus cards which uses SMD ram (there is no 2 MB TTH version).  The 1 MB TTH version is probably the easiest to get working but it is too tall for the ML09 case.

2 MB Agnus card: https://github.com/gazzmaniac/SMD2000_Agnus2MB 

1 MB SMD Agnus card: https://github.com/gazzmaniac/SMD2000_Agnus_1MB 


## Licensing
Design is open source hardware.
1. Any and all derivative designs must also be open source.
2. No person, business, or other entity associated with this design shall be liable for any damages incurred by anyone as a result of using this design.  If you do not accept this condition do not build the project.
3. Free for private use by anyone.
4. Free for anyone to make for sale by anyone.
5. CERN Open Hardware Licence Version 2 - Strongly Reciprocal CERN-OHL-S) license applies, subject to conditions 1-4 above.
6. Any portions of this design from other projects shall be licensed according to their respective licenses if their licenses are not compatible with CERN-OHL-S or the conditions above.
7. All Other Rights Reserved.

## Requirements
To make a complete SMD2000 you also need to build a motherboard and a CPU card.  They are documented separately.

The SMD2000 project requires a donor Amiga, either an A500, A500+, A2000, or A600 plus a Gary.

If you intend to use the Kicad files you will need the SMD2000 symbol and footprint libraries.  They are included in the SMD2000 motherboard package.  You will probably need to change the path in Kicad.

## Notes and Eratta
X1, the 28.37516 oscillator (for PAL systems) is difficult to find new.  Most constructors will probably use the one from the donor board.  I had success buying them from AliExpress, testing with the frequency function on the oscilloscope gave values of 28.3752 which is correct to the limits of accuracy of the scope.  

Jumpers have same function as those wih same numbers on A2000.
JP101 determines the memory location of the second 512 kb of ram by connecting Agnus A19 signal to either CPU A23 (1-2) or A19 (2-3), which in turn determines whether it is chip ram or slow ram ("ranger ram").  
It comes configured to A19 (2-3), configuring the ram as chip ram mapped at $0800000.  Change to 1-2 if using a 512 kb Agnus (8370 or 8371) to configure as slow ram at $C00000.  You will also need to close J500 on the motherboard.

RAM is 256k x4 as found on later A2000 and A500 motherboards and many A501 compatible ram expansions.

Take extra care to ensure the connector is the correct orientation for the connector on the motherboard.

## Notes about Agnus revisions
This board is designed for the 8372A 1MB ECS FAT AGNUS from later A500 and A2000 (tested and verified) and 512k OCS 8370/8371 Agnus from early A500/A2000 (not verified but no reason it won't work).  It may work with 2MB 8372AB and 8372B (A3000) Agnus but there will only be 1 mb ram.

The 2 MB 8375 Agnus from the A500+ and A600 have a different pinout and WILL NOT WORK.  Use the 8375 2 MB Agnus Board if you have one of them.

The 8375 Agnus ICs are not all the same.  Some have the same pinout as 8372A (Commodore made them as spare parts).  They can be identified by "VBB" marking.  Also check the Commodore part numbers:
318069-16 and 318069-17 - 8372A equivalent (1MB)
318069-18 and 318069-19 - 8372B equivalent (2MB)
These 8375 Agnuses required a field mod to work properly: removal of R101 and addition of a 0.1 uF capacitor.  Provision for this capacitor is made in the SMD 2000.  Check table below:

| AGNUS	|	JP101	| R101	|	C103	|	J102 |
|-------|-------|-------|-------|------|
| 8370/8371:	|	1-2	| Installed	| Not Installed	| OPEN PAL/CLOSED NTSC |
| 8372:	| 2-3	| Installed	| Not Installed	| OPEN PAL/CLOSED NTSC |
| Pin Compatible 8375:	| 2-3	| Not Installed	| Installed	| OPEN |
| 8375 from A500+/A600:	| USE | OTHER | AGNUS | BOARD! |


## References
Amiga A500/A2000 Technical Reference Manual

A2000 schematics (Commodore scanned and Amigawiki.org vector)

Agnus Revision Information:
https://www.amigawiki.org/lib/exe/fetch.php?media=de:parts:agnus_reworks.pdf
https://bigbookofamigahardware.com/bboah/product.aspx?id=1478

Datasheet for HYB514256B (4x256kbit RAM)
Various component data sheets.  Refer component metadata.
