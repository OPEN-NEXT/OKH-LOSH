Representative metadata for OSH
=

# Intro

As documentation is technology-specific, reasonable metadata may be as well. 

This first draft:
- assumes that metadata must be technology-specific in order to give a meaningful representation and hence enable meaningful connections between OSH modules;
- allows different levels of compliance:
  - Level 1: Connecting to the OSHI\
  …by providing
    - [OKH-MOD](#osh-module-okh-mod)
  - Level 2: Enabling decentralised production\
  …by providing
    - [OKH-MOD](#osh-module-okh-mod)
    - OKH-OSH

# OSH Module (OKH-MOD)

**Intro:**

- = assembly of components (and subassemblies) with clear input, output and interfaces 
  - (and thus can be used independently from the rest of the original machine as far as required inputs and interfaces are respected);
- metadata shall represent functionality and "position inside the OSH ecosystem" (→ BoM = link to other modules)

**Metadata:**

- name or working title
- version
    - of hardware design
    - of documentation
- link to [OKH-ASM](#osh-assembly-okh-asm) (manifest file for assemblies)
- link to LICENSE.md
- link to README.md
- link to CONTRIBUTING.md
- functional description (e.g. what functions it is supposed to deliver, what is the problem it solves, for whom etc.)
    - → use guidelines for naming convention e.g. [as for inventions](https://www.wipo.int/export/sites/www/standards/en/pdf/03-15-01.pdf)
    - description of input, output and interfaces
- link to [standardised BoM](#standardised-bom)
- (link to) functional metadata ← _very_ technology-specific! not to be standardised here
  - dimensions
  - material
  - weight
  - RPM
  - …

## standardised BoM

= for documentation purposes; easy to read, crawl and use (maybe call **meta-BoM**?)

| Pos. | Name         | Units | Type            | Reference                                 |
|------|--------------|-------|-----------------|-------------------------------------------|
| 1    | casing       | 2     | OSH Component   | link to [OKH-OSH](#piece-of-osh-okh-osh)  |
| 2    | screw        | 4     | standard part   | standard designation                      |
| 3    | gear box     | 1     | OSH Module      | link to [OKH-MOD](#osh-module-okh-mod)    |
| 4    | Raspberry Pi | 1     | purchased part  | unambiguous reference (not standardised)  |
| 5    | bracket      | 2     | OSH Subassembly | link to [OKH-OSH](#piece-of-osh-okh-osh)  |

**Note:** In case the author(s) prefer level-1-compliance, OKH-OSH can be omitted.

# Piece of OSH (OKH-OSH)

**Intro:**

- = component or assembly of components
- metadata shall enable reproduction, modification, operation and maintenance

**Metadata:**

- name or working title
- version
  - of hardware design
  - of documentation
- applying technology-specific documentation criteria ([TsDC-IDs](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-DB-print.md))
- links to files required by TsDC\
= technology-specific block

Some examples:\
(unaltered metadata are *italic*)

## mechanical component (OKH-MEC)

- *name or working title*
- *version*
  - *of hardware design*
  - *of documentation*
- *applying technology-specific documentation criteria ([TsDC-IDs](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-DB-print.md))*
- links to design files
    - 3D model
        - source (→ script gets file format)
        - export (STD)
    - 2D drawing
        - source (→ script gets file format)
        - export (PDF)
- links to additional files (e.g. manufacturing instructions, justification of technical design)

## PCB (OKH-ASM-PCB)

- *name or working title*
- *version*
  - *of hardware design*
  - *of documentation*
- *applying technology-specific documentation criteria ([TsDC-IDs](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-DB-print.md))*
- links to design files
  - bill of materials
  - circuit diagram
  - PCB overlay diagram
  - gerber file