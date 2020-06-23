# Representative metadata for OSH

## Intro

As documentation is technology-specific, reasonable metadata may be as well.

This first draft:

- assumes that metadata _must_ be technology-specific in order to give a meaningful representation and hence enable meaningful connections between OSH modules;
- organises metadata in a modular approach;
- allows different levels of compliance:
  - **Level 1: Connecting to the [OSHI](README.md)**\
  …by providing
  - [OSH-Module](#osh-module)
    - **Note:** `link to simplified BoM` will be just substituted by a link to the documentation release then.
  - **Level 2: Enabling decentralised production**\
  …a piece of hardware is then (in L2 compliance) represented by
    - [OSH-Module](#osh-module)\
    which links to
    - [simplified BoM](#simplified-bom-sbom)\
    which links to
    - standard/purchased parts via unambiguous references
    - [POSHs](#piece-of-osh-posh) design files\
    which link to design files

**File location convention:** To be clarified (see [this issue](https://github.com/OPEN-NEXT/OSHI/issues/5))

**Naming convention:**  To be clarified (see [this issue](https://github.com/OPEN-NEXT/OSHI/issues/5))

## Details

Wikidata's ontology, which is based on [OWL 2](https://www.w3.org/TR/owl2-rdf-based-semantics/)

<!---
TBC:

- sBoM is no longer input but an optional of the OSHI
  - relation between OSHMs and POSHs can be easily shown with an extra field 'part of'
- for better readability, the following section may start with "properties" describing all slots, followed by OSHM, POSH etc. just containing the slot names
--->

### OSH-Module

**Intro:**

- = assembly of components (and subassemblies) with clear input, output and interfaces
  - (and thus can be used independently from the rest of the original machine as far as required inputs and interfaces are respected);
- metadata shall represent functionality and "position inside the OSH ecosystem" (→ BoM = link to other modules)

**Metadata:**

- type: class
- slots [data type]
  - name or working title [String]
  - version [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)]
    - = unambiguous reference of the version of the hardware design and the version of the documentation
    - e.g. a manually given version number or a commit hash
  - function [String]
    - functional description, e.g. what it actually does, what problem it solves, for whom, under which conditions etc.
    - optional: description of input, output and interfaces
  - function-category [xxx]
    - preferably use existing DBs like wikibase
  - (multiple) consists-of [URL]
    - links to metadata files of POSHS and other OSHMs this OSHM consists of
  - license [URL]
    - link to LICENSE.md or legal code of the license
  - readme [URL]
    - link to README.md or general description
  - status [String]
    - development status, preferably use defined designations like:
      - development
      - prototype
      - certified
      - in production
  - (optional) certificate [URL]
    - link to certificate (OSHWA, DIN SPEC 3105)
  - (optional) contributing [URL]
    - link to CONTRIBUTING.md
  - (optional, multiple) standards [String]
    - standards used in the _design_ (not DIN SPEC 3105-1)
  - (optional, multiple) functional-metadata **(← _very_ technology-specific! not to be standardised here)** [String]
    - dimensions
    - material
    - weight
    - RPM
    - …
- (multiple) TsDC [String]
  - applying [TsDC-IDs](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-DB-print.md)
- [links to files required by TsDC]\
= technology-specific block

**COMMENT:** manufacturres, funders, standards etc. would be on the same level as `OSH Module`

### simplified BoM (sBoM)

**Intro:**

- meant to be easy to read, crawl and use
- references to all parts and files necessary to build the [OSH-Module](#osh-module) following [TsDC](https://gitlab.com/OSEGermany/oh-tsdc/)-requirements
  - column `Reference` includes single entries only which are either
    - URLs to a [POSH](#piece-of-osh-posh)
    - unambiguous references to standard or purchased parts (which can be either URLs or designations)
    - URLs to other [OSH-Modules](#osh-module)
- subassemblies are _not_ represented as individual modules, but included via structured pos. numbers

EXAMPLE:

[**This section is OUTDATED; simplified BoMs now may include subassemblies via appropriate pos. numbers which makes linking to ASM-specific metadata files obsolete**]

| Pos. | Name         | Units | Type            | Reference                                                                           |
|------|--------------|-------|-----------------|-------------------------------------------------------------------------------------|
| 1    | casing       | 2     | OSH Component   | link to [POSH file](#piece-of-osh-posh), similar to [this](#mechanical-component-posh-mec) one                                      |
| 2    | screw        | 4     | standard part   | standard designation                                                                |
| 3    | gear box     | 1     | OSH Module      | link to [OSH-Module](#osh-module)                                                   |
| 4    | Raspberry Pi | 1     | purchased part  | unambiguous reference (not standardised)                                            |
| 5    | holder       | 1     | OSH Subassembly | link to [POSH file](#piece-of-osh-posh), similar to [this](#mechanical-component-posh-mec) one                                      |
| 5.1  | bracket      | 2     | OSH Component   | link to [POSH file](#piece-of-osh-posh), similar to [this](#mechanical-component-posh-mec) one                                      |
| 5.2  | screw        | 2     | standard part   | standard designation                                                                |
| 5.3  | arm          | 2     | OSH Component   | link to [POSH file](#piece-of-osh-posh), similar to [this](#mechanical-component-posh-mec) one                                      |
| 6    | controller   | 1     | OSH Module      | link to link to [OSH-Module](#osh-module), similar to [this](#pcb-posh-asm-pcb) one |

### Piece of OSH (POSH)

**Intro:**

- = component or assembly of components
- metadata shall enable decentralised production, modification, oper  ation and maintenance
- …and facilitate 'packaging' (=find the files you actually need)

**Metadata:**

- type: subclass of [OSH-Module](#osh-module)
- slots [data type]
  - name or working title [String]
  - documentation release [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)]
    - = unambiguous reference of the version of the hardware design and the version of the documentation
- (multiple) applying [TsDC-IDs](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-DB-print.md) [String]
- links to files required by TsDC\
= technology-specific block

## Examples

[**The following section is OUTDATED; but shouldn't be too wrong anyway**]

(unaltered metadata are *italic*)

### mechanical component (POSH-MEC)

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
- for production:
  - outer dimensions (dimension+shape+measures e.g. mm-ø20x100 for a cylindric thing)
  - tolerance class (according to ISO XXX)
  - surface finish (according to ISO XXX)
  - material
  - manufacturing technology (machining, additive, forming, casting,…)

### mechanically joined assembly (POSH-ASM-MEC)

xxx

### PCB (POSH-ASM-PCB)

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
