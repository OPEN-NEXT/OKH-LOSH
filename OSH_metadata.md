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

## Meta-requirements

### Location and Naming Convention

The file name:

1. must contain `OKH`
   1. this is sufficient for our crawler to identify it,
   2. however you may add whatever you like in this name (e.g. as required in the [OKH Manifest Specification v1.0](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1) `OKH-thingname`)
2. must start with a dot, → so e.g. `.okh.yml`
   - …so files don't get changed unintentionally they will be hidden on Linux-based systems so the local folder looks neater and it's easier for the crawler to identify these files

The metadata file describing the whole OSH Module **must be placed in the root directory**; all metadata files for sub-modules or components may be placed in the corresponding folder so that they would be in the root directory if the module would be cloned into a individual repository.\
However as files are unambiguously referenced in the OSHM file you can place them wherever you like.

### File Formats

To connect your OSH to the OSHI, your metadata must be stored in one of the following formats:

- YAML
- TOML
- JSON

Please use the linked templates to enter your data.

Background:\
The crawler will take this metadata as basic input, add additional information to it (e.g. from the Gitlab API) and build a TTL file with all that information which is then integrated in Wikibase.
You see, it doesn't really matter in which file format you'll save your metadata as long as the crawler is able to interpret it.

## Details

Wikidata's ontology, which is based on [OWL 2](https://www.w3.org/TR/owl2-rdf-based-semantics/)

### Classes & Slots

#### Classes

- OSHM [class]
  - [OSH Module](#osh-module)
- POSH [class]
  - [Piece of Open Source Hardware](#piece-of-osh-posh)

#### Slots/Properties [data type]

- class
- name [String]
  - working title
  - designation for POSH, standard or purchased component
- owner [String]
  - organisation/individual behind the hardware design
- language [String]
  - language in which the documentation is written
- version [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)]
  - = unambiguous reference of the version of the hardware design and the version of the documentation
  - e.g. a manually given version number or a commit hash
- function [String]
  - functional description, e.g. what it actually does, what problem it solves, for whom, under which conditions etc.
  - optional: description of input, output and interfaces
- function-category [String]
  - preferably use existing DBs like wikidata
  - can be multiple
- sBoM [URL]
  - links to a CSV containing all POSHS and other OSHMs this OSHM consists of
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
- attestation [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)]
  - link to certificate (OSHWA, DIN SPEC 3105)
- contributing [URL]
  - link to CONTRIBUTING.md
- standard [String]
  - standard used/considered in the _design_ (not DIN SPEC 3105-1)
- functional-metadata **(← _very_ technology-specific! not to be standardised here)** [String]
  - dimensions
  - material
  - weight
  - RPM
  - …
- production-metadata [String]
  - outer dimensions (dimension + (measuere type+)measures e.g. mm-ø20x100 for a cylindric thing)
    - cuboid (mm-100x50x20)
    - cylinder (mm-ø50x100)
    - sphere (mm-ø15)
  - smallest tolerance
    - preferrably use designation according to ISO 286-1:2010
  - finest surface roughness in µm
  - material
  - manufacturing technology (machining, additive, forming, casting,…)
- TsDC [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)]
  - applying [TsDC-IDs](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-DB-print.md)
- source-3d [URL]
  - e.g. CAD model
- source-2d [URL]
  - e.g. drawing, gerber file (all in the original file format)
- source+ [URL]
  - additional technical documentation
  - as required by TsDC
  - e.g. manufacturing instructions, post-processing specifications (e.g. as MD files)
- export-3d [URL]
  - e.g. STEP
- export-2d [URL]
  - e.g. PDF files
- export+ [URL]
  - e.g. PDF files
- quantity [quantity](https://www.wikidata.org/wiki/Property:P1114)
- reference [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)]
  - for standard or purchased components

### Required Metadata

#### simplified BoM (sBoM)

**Intro:**

- meant to be easy to read, crawl and use
- references to all parts and files necessary to build the [OSH-Module](#osh-module) following [TsDC](https://gitlab.com/OSEGermany/oh-tsdc/)-requirements
  - column `Reference` includes single entries only which are either
    - URLs to a [POSH](#piece-of-osh-posh)
    - unambiguous references to standard or purchased parts (which can be either URLs or designations)
    - URLs to other [OSH-Modules](#osh-module)
- subassemblies are _not_ represented as individual modules, but included via structured pos. numbers

**Location and Naming Convention:**

- to be stored as CSV in the same level as the metadata file linking to this sBoM
- name *must* contain `sBoM`

**EXAMPLE:**

| Pos. | Name         | Units | Type            | Reference                                                                           |
|------|--------------|-------|-----------------|-------------------------------------------------------------------------------------|
| 1    | casing       | 2     | POSH   | link to [POSH file](#piece-of-osh-posh), similar to [this](#mechanical-component-posh-mec) one                                      |
| 2    | screw        | 4     | standard part   | standard designation                                                                |
| 3    | gear box     | 1     | OSHM     | link to [OSH-Module](#osh-module)                                                   |
| 4    | Raspberry Pi | 1     | purchased part  | unambiguous reference (not standardised)                                            |
| 5    | holder       | 1     | POSH | link to [POSH file](#piece-of-osh-posh), similar to [this](#mechanical-component-posh-mec) one                                      |
| 5.1  | bracket      | 2     | POSH   | link to [POSH file](#piece-of-osh-posh), similar to [this](#mechanical-component-posh-mec) one                                      |
| 5.2  | screw        | 2     | standard part   | standard designation                                                                |
| 5.3  | arm          | 2     | POSH   | link to [POSH file](#piece-of-osh-posh), similar to [this](#mechanical-component-posh-mec) one                                      |
| 6    | controller   | 1     | OSHM      | link to link to [OSH-Module](#osh-module), similar to [this](#pcb-posh-asm-pcb) one |

#### OSH Module (OSHM)

**Intro:**

- = assembly of components (and subassemblies) with clear input, output and interfaces
  - (and thus can be used independently from the rest of the original machine as far as required inputs and interfaces are respected);
- metadata shall represent functionality and "position inside the OSH ecosystem" (→ BoM = link to other modules)

**Metadata:**

- name
- organisation
- language
- version
- function
- function-category
- sBoM
- license
- readme
- certificate
- contributing
- standard (multiple)
- functional-metadata (multiple)
- TsDC (multiple)
- source-3d
- source-2d
- source+
- export-3d
- export-2d
- export+

**COMMENT:** manufacturres, funders, standards etc. would be on the same level as `OSH Module`

#### Piece of OSH (POSH)

**Intro:**

- = component or assembly of components
- metadata shall enable decentralised production, modification, operation and maintenance
- …and facilitate 'packaging' (=find the files you actually need)

**Metadata:**

- name
- version
- standard (multiple)
- TsDC (multiple)
- source-3d (multiple)
- source-2d (multiple)
- source+ (multiple)
- export-3d (multiple)
- export-2d (multiple)
- export+ (multiple)
- production-metadata

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

## additional information added by crawler

- file formats
  - to be parsed from source URLs
- status
  - to be assessed judging from version (0.x.x; beta) or source URL (dev branch) or the presence of an attestation URL
- version/fork/variant of another OSHM/POSH
  - version, URL, presence of other _very_ similar OSH in the knowledge base (judging e.g. from 'consists of'), information from the GitHub/Gitlab API ('fork of' etc.)
- joining technology
  - by TsDC-ID
- check references in [sBoM](#simplified-bom-sbom) for ambiguity
- assign classes to instances
  - by sBoM `Types` column
