Representative metadata for OSH
=

# Intro

As documentation is technology-specific, reasonable metadata may be as well. 

This first draft:
- assumes that metadata _must_ be technology-specific in order to give a meaningful representation and hence enable meaningful connections between OSH modules;
- organises metadata in a modular approach;
- allows different levels of compliance:
  - **Level 1: Connecting to [the OSHI](README.md)**\
  …by providing
    - [OKH-MOD](#osh-module)
    - **Note:** `link to simplified BoM` will be just substituted by a link to the documentation release then.
  - **Level 2: Enabling decentralised production**\
  …by providing
    - [OKH-MOD](#osh-module)
    - [simplified BoM](#simplified-bom)
    - OKH-OSH

# Details 

## OSH Module (OKH-MOD)

**Intro:**

- = assembly of components (and subassemblies) with clear input, output and interfaces 
  - (and thus can be used independently from the rest of the original machine as far as required inputs and interfaces are respected);
- metadata shall represent functionality and "position inside the OSH ecosystem" (→ BoM = link to other modules)
- this file is the main reference for OSH modules (**not** [OKH-OSH](#piece-of-osh-okh-osh) (manifest file for assemblies))

**Metadata:**

- name or working title
- version of documentation release (mentioning the version of the hardware design)
- link to [OSH-Module](#piece-of-osh-okh-osh) (manifest file for components & assemblies)
  - **Note:** In case the author(s) prefer level-1-compliance, OKH-OSH can be substituted by a link to the documentation release.
- link to LICENSE.md
- link to README.md
- link to certificate (OSHWA, DIN SPEC 3105)
- link to CONTRIBUTING.md
- functional description (e.g. what functions it is supposed to deliver, what is the problem it solves, for whom etc.)
    - → use guidelines for naming convention e.g. [as for inventions](https://www.wipo.int/export/sites/www/standards/en/pdf/03-15-01.pdf)
    - description of input, output and interfaces
  - standards used in design
- (link to) functional metadata ← _very_ technology-specific! not to be standardised here
  - dimensions
  - material
  - weight
  - RPM
  - …

## simplified BoM

**Intro:**

- = for documentation purposes; easy to read, crawl and use
- to be used whenever a BoM is required in the technology-specific block of [OKH-OSH](#piece-of-osh-okh-osh)

EXAMPLE:

| Pos. | Name         | Units | Type            | Reference                                 |
|------|--------------|-------|-----------------|-------------------------------------------|
| 1    | casing       | 2     | OSH Component   | link to [OKH-OSH](#piece-of-osh-okh-osh)  |
| 2    | screw        | 4     | standard part   | standard designation                      |
| 3    | gear box     | 1     | OSH Module      | link to [OKH-MOD](#osh-module-okh-mod)    |
| 4    | Raspberry Pi | 1     | purchased part  | unambiguous reference (not standardised)  |
| 5    | bracket      | 2     | OSH Subassembly | link to [OKH-OSH](#piece-of-osh-okh-osh)  |

## Piece of OSH (OKH-OSH)

**Intro:**

- = component or assembly of components
- metadata shall enable reproduction, modification, operation and maintenance

**Metadata:**

- name or working title
- version of documentation release (mentioning the version of the hardware design)
- applying technology-specific documentation criteria ([TsDC-IDs](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-DB-print.md))
- links to files required by TsDC\
= technology-specific block

Some examples:\
(unaltered metadata are *italic*)

### mechanical component (OKH-MEC)

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
- optional fields:
  - tolerance class (according to ISO XXX)
  - surface finish (according to ISO XXX)
  - material

### PCB (OKH-ASM-PCB)

- *name or working title*
- *version*
  - *of hardware design*
  - *of documentation*
- *applying technology-specific documentation criteria ([TsDC-IDs](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-DB-print.md))*
- links to design files
  - [simplified BoM](#simplified-bom)
  - circuit diagram
  - PCB overlay diagram
  - gerber file

# annotated template

Basis: [OWL 2](https://www.w3.org/TR/owl2-rdf-based-semantics/)

## OSH-Module
- type: class
- slots [data type]
  - name or working title [String]
  - documentation release [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)] 
  - functional description [String] 
    - e.g. what it actually does, what problem it solves, for whom, under which conditions etc.
    - description of input, output and interfaces **(← cross out?)**
  - link to [simplified BoM](#simplified-bom) [URL]
  - link to LICENSE.md [URL]
  - link to README.md [URL]
  - (optional) link to certificate (OSHWA, DIN SPEC 3105) [URL]
  - (optional) link to CONTRIBUTING.md [URL]
  - (optional) standards used in the design [[list](https://www.wikidata.org/wiki/Q27948)]
  - (optional) list of functional metadata **(← _very_ technology-specific! not to be standardised here)** [[list](https://www.wikidata.org/wiki/Q27948)]
    - dimensions
    - material
    - weight
    - RPM
    - …

**COMMENT:** manufacturres, funders, standards etc. would be on the same level as `OSH Module`