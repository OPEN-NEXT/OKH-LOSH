Representative metadata for OSH
=

# Intro

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
  …a piece of hardware is then (in L2 compliance) represented by\
    - [OSH-Module](#osh-module)\
    which links to
    - [simplified BoM](#simplified-bom-sbom)\
    which links to
    - standard/purchased parts via unambiguous references
    - [POSHs](#piece-of-osh-posh) design files\
    which link to design files

**File location convention:** To be clarified
- saving all files in the root level may create a mess
- saving files in the same level as the corresponding hardware design file may not be possible in all cases as repositories are sometimes a mess
- suggestion 1: saving all files in a "OKH" folder in the root level
- suggestion 2: squash everything into one huge TTL ← _very_ hard to mantain for large assemblies, I guess
- suggestion 3: OSH-Module file is named "OKH" and placed in the root folder; name the files however you like and store them wherever this fits your needs – as they are linked, this shouldn't affect anything
    - we suggest you name files after the type of the corresponding hardware position number in the BoM (e.g. OKH-POSH-MEC-5-1.TTL) and place them in the root folder of the corresponding (sub-)assembly or component

**Naming convention:** To be clarified
- should be as easy & fast as possible; "okh-thingname.yml" as suggested in [OKHv1.0](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1) isn't convenient in practice
- however, when saving all files in one root-level folder those files should carry some kind of human-readable identifier in their name
- copy of suggestion 3: OSH-Module file is named "OKH" and placed in the root folder; name the files however you like and store them wherever this fits your needs – as they are linked, this shouldn't affect anything
    - we suggest you name files after the type of the corresponding hardware position number in the BoM (e.g. OKH-POSH-MEC-5-1.TTL) and place them in the root folder of the corresponding (sub-)assembly or component

# annotated template

Basis: [OWL 2](https://www.w3.org/TR/owl2-rdf-based-semantics/)

## OSH-Module

**Intro:**

- = assembly of components (and subassemblies) with clear input, output and interfaces 
  - (and thus can be used independently from the rest of the original machine as far as required inputs and interfaces are respected);
- metadata shall represent functionality and "position inside the OSH ecosystem" (→ BoM = link to other modules)

**Metadata:**

- type: class
- slots [data type]
  - name or working title [String]
  - documentation release [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)]
    - = unambiguous reference of the version of the hardware design and the version of the documentation
  - functional description [String] 
    - e.g. what it actually does, what problem it solves, for whom, under which conditions etc.
    - description of input, output and interfaces **(← cross out?)**
  - link to [sBoM](#simplified-bom-sbom) [URL]
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
- applying [TsDC-IDs](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-DB-print.md) [List]
- links to files required by TsDC\
= technology-specific block


**COMMENT:** manufacturres, funders, standards etc. would be on the same level as `OSH Module`

## simplified BoM (sBoM)

**Intro:**

- meant to be easy to read, crawl and use
- references to all parts and files necessary to build the [OSH-Module](#osh-module) following [TsDC](https://gitlab.com/OSEGermany/oh-tsdc/)-requirements
  - column `Reference` includes single entries only which are either
    - URLs to a [POSH](#piece-of-osh-posh)
    - unambiguous references to standard or purchased parts (which can be either URLs or designations)
    - URLs to other [OSH-Modules](#osh-module)
- subassemblies are _not_ represented as individual modules, but included via structured pos. numbers

EXAMPLE:

**This section is OUTDATED; simplified BoMs now may include subassemblies via appropriate pos. numbers which makes linking to ASM-specific metadata files obsolete**

| Pos. | Name         | Units | Type            | Reference                                                   |
|------|--------------|-------|-----------------|-------------------------------------------------------------|
| 1    | casing       | 2     | OSH Component   | link to [OKH-OSH](#piece-of-osh-okh-osh)                    |
| 2    | screw        | 4     | standard part   | standard designation                                        |
| 3    | gear box     | 1     | OSH Module      | link to [OSH-Module](#osh-module)                           |
| 4    | Raspberry Pi | 1     | purchased part  | unambiguous reference (not standardised)                    |
| 5    | holder       | 1     | OSH Subassembly | link to [OKH-OSH](#piece-of-osh-okh-osh)                    |
| 5.1  | bracket      | 2     | OSH Component   |                                                             |
| 5.2  | screw        | 2     | standard part   |                                                             |
| 5.3  | arm          | 2     | OSH Component   |                                                             |
| 6    | controller   | 1     | OSH Module      | link to link to [OSH-Module](#osh-module) #pcb-posh-asm-pcb |

## Piece of OSH (POSH)

**Intro:**

- = component or assembly of components
- metadata shall enable decentralised production, modification, operation and maintenance
- …and facilitate 'packaging' (=find the files you actually need)

**Metadata:**

- type: subclass of [OSH-Module](#osh-module)
- slots [data type]
  - name or working title [String]
  - documentation release [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)]
    - = unambiguous reference of the version of the hardware design and the version of the documentation
- applying [TsDC-IDs](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-DB-print.md) [List]
- links to files required by TsDC\
= technology-specific block

Some examples:\
(unaltered metadata are *italic*)

# Examples
**The following section is OUTDATED; but shouldn't be too wrong anyway**

## mechanical component (POSH-MEC)

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

## PCB (POSH-ASM-PCB)

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