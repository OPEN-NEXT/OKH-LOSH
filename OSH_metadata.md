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

### Classes & Slots

#### Classes

- OSHM [class]
  - [OSH Module](#osh-module)
- POSH [class]
  - [Piece of Open Source Hardware](#piece-of-osh-posh)
- POSH+(TsDC-ID) [subclass]

#### Slots/Properties [data type]

- name [String]
  - working title
- version [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)]
  - = unambiguous reference of the version of the hardware design and the version of the documentation
  - e.g. a manually given version number or a commit hash
- function [String]
  - functional description, e.g. what it actually does, what problem it solves, for whom, under which conditions etc.
  - optional: description of input, output and interfaces
- function-category [String]
  - preferably use existing DBs like wikidata
  - can be multiple
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
- (multiple) TsDC [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)]
  - applying [TsDC-IDs](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-DB-print.md)
- [links to files required by TsDC] [URL]\
= technology-specific block

### Required Metadata

#### OSH Module (OSHM)

**Intro:**

- = assembly of components (and subassemblies) with clear input, output and interfaces
  - (and thus can be used independently from the rest of the original machine as far as required inputs and interfaces are respected);
- metadata shall represent functionality and "position inside the OSH ecosystem" (→ BoM = link to other modules)

**Metadata:**

- name
- version
- function
- function-category
- consists-of (multiple)
- license
- readme
- status
- certificate (optional)
- contributing (optional)
- standards (optional, multiple)
- functional-metadata (optional, multiple)
- TsDC (multiple)
- [links to files required by TsDC]\
= technology-specific block

**COMMENT:** manufacturres, funders, standards etc. would be on the same level as `OSH Module`

#### Piece of OSH (POSH)

**Intro:**

- = component or assembly of components
- metadata shall enable decentralised production, modification, operation and maintenance
- …and facilitate 'packaging' (=find the files you actually need)

**Metadata:**

- name
- version
- TsDC (multiple)
- [links to files required by TsDC]\
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
