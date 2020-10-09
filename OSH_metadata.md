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

#### A MOSH file

1. is named `.okh`\
  (note the dot\
  …so the file won't get changed unintentionally & it will be hidden on Linux-based systems which gives a neater look & it's easier for the crawler to identify these files);
2. is located in the root directory of the [OSH Module](#osh-module-MOSH).

#### A POSH file

1. is named `.okh-<anything>`\
  while `<anything>` is replaced by any type of identifier (e.g. a short name)\
  (note the dot);
2. should be stored in reasonable ways (e.g. in the folder containing the design files)
  for a intuitive repo structure (e.g. so   people get also the metadata file when they clone just this component).\
  However as files are unambiguously referenced in the MOSH file you can place them wherever you like.

### File Formats

To connect your OSH to the OSHI, your metadata must be stored in one of the following formats:

- [JSON-LD](https://json-ld.org/)
- YAML (for OKHv1 **only**)
- We may allow more file formats in the future as everything is converted and uploaded to the Wikibase instance anyway.

Please use the linked templates to enter your data.

Background:\
The crawler will take this metadata as basic input, add additional information
to it (e.g. from the Gitlab API), build a JSON file with all that information
and uploads it to Wikibase via a Data Input API (developed by WMDE). It doesn't
really matter in which file format you'll save your metadata as long as the
crawler is able to interpret it.

## Ontology

Mostly Wikidata's ontology, which is based on [OWL 2](https://www.w3.org/TR/owl2-rdf-based-semantics/)

We'll use Wikidata's terms:

| Wikidata term | term in other resources |
| --- | --- |
| class | class |
| property | slot/feature/attribute |
| qualifier | facet |

### Classes & Slots

#### Classes

- class [[class](https://www.wikidata.org/wiki/Property:P2308)]
  - [MOSH](#osh-module-MOSH)
  - [POSH](#piece-of-osh-posh)
  - STD – standard component
  - BUY – purchased component

#### Slots/Properties [data type]

**Legend:**

- property [data format] | [[wikidata equivalent]([wikidata.org](https://www.wikidata.org/wiki/Wikidata:List_of_properties))]\
  some description
  - qualifyer | [[wikidata equivalent]([wikidata.org](https://www.wikidata.org/wiki/Wikidata:List_of_properties))]

- property [rdfs:range data/object → xx] | [[wikidata equivalent]([wikidata.org](https://www.wikidata.org/wiki/Wikidata:List_of_properties))]\
  some description
  - qualifyer | [[wikidata equivalent]([wikidata.org](https://www.wikidata.org/wiki/Wikidata:List_of_properties))]

---

- [x] attestation [URL]
  - link to official confirmation of compliance (OSHWA, FSF, DIN SPEC 3105)
- export [URL]\
  URL to exported source files in a data format that is generally accessible to recipients
  (e.g [technical drawing](https://www.wikidata.org/wiki/Q192521) or [3d model](https://www.wikidata.org/wiki/Property:P4896)), gerber file etc.)\
  e.g. PDF, STL, STP
  - qualifiers are defined [here](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-explanatory.md)
- [x] file-format | [[file format](https://www.wikidata.org/wiki/Property:P2701)]
  - property of `export`, `source` (and all their subproperties)
- [x] fork-of | [[based on](https://www.wikidata.org/wiki/Property:P144)]\
  specify source project this project has been forked from
- [x] function [string] | [[scope and content](https://www.wikidata.org/wiki/Property:P7535)]\
  functional description, e.g. what it actually does, what problem it solves, for whom, under which conditions etc.\
  so if you whish that someone finds & uses your MOSH specifically e.g. for
  COVID-19-crisis response, include relevant keywords in this field\
  optional: description of input, output and interfaces
- [x] functional-metadata [[supported metadata](https://www.wikidata.org/wiki/Property:P8203)]
  - _very_ technology-specific, not to be standardised here
  - dimensions
  - material
  - weight
  - RPM
  - …
- [x] image [URL] | [[Commons compatible image available at URL](https://www.wikidata.org/wiki/Property:P4765)]
  - URL to a meaningful picture of this module
  - license must be clear under this URL
  - to be displayed on the OHO project page when found by a search in Wikibase
- [x] IPC\
  International Patent Classification\
  international, stable category system for projects in the patent domain (as OSH)
- [x] language | [[IETF language tag](https://www.wikidata.org/wiki/Property:P305)]\
  tag for the language in which the documentation is available using IETF
  language tags following the BCP 47 standard), such as `en` or `en-GB`
- [x] alternative-license [URL] | [[copyright license](https://www.wikidata.org/wiki/Property:P275)] ← but different data type
  - URL to legal code of the license (e.g. LICENSE.md) in case SPDX identifier is not existent
- [x] spdx-license [string] | [[SPDX license identifier](https://www.wikidata.org/wiki/Property:P2479)]
- [x] name [string] | [[name](https://www.wikidata.org/wiki/Property:P2561)]\
  working title\
  designation for POSH, standard or purchased component
- [x] okhv\
  version of the metadata standard used in this file
- [x] owner | [[copyright holder](https://www.wikidata.org/wiki/Property:P3931)]
  - organisation/individual behind the hardware design
- [x] parent-asm | [[part of](https://www.wikidata.org/wiki/Property:P361)]
  - identifies the assembly/module the component is part of
- [x] production-metadata | sort of: [[supported metadata](https://www.wikidata.org/wiki/Property:P8203)]\
  yet to be specified; e.g. (NOT QUALIFIERS ↓)
  - outer dimensions (dimension + (measuere type+)measures e.g. mm-ø20x100 for a cylindric thing)
    - cuboid (mm-100x50x20)
    - cylinder (mm-ø50x100)
    - sphere (mm-ø15)
  - smallest tolerance
    - preferrably use designation according to ISO 286-1:2010
  - finest surface roughness in µm
  - material
  - manufacturing technology (machining, additive, forming, casting,…)
- [x] quantity | [quantity](https://www.wikidata.org/wiki/Property:P1114)\
  quantity of a component in the `parent-asm`
- [x] readme [URL]\
  link to general project description; may be the project webpage, may be the `README.md`\
  to be displayed on the OHO project page when found by a search in Wikibase
- [x] repo [[URL]\
  URL to development channel\
  people will use this URL to start contribution
  (reporting issues, giving feedback, joining the development)
- [x] reference
  - buy-reference [string]
    - unambiguous reference for non-standard purchased components
    - others shall be able to identify/procure this component only by the given reference(s)
  - standard-designation [string]
    - unambiguous reference for a standard component (preferably naming the latest standard)
    - connection point for the future library of standard components (→ automatic checking for unambiguous referencing)
  - reference URL
    - <https://www.wikidata.org/wiki/Property:P854>
- [x] sBoM [URL]\
  simplified Bill of Materials to identify components of this module (MOSH)
  - links to a CSV containing all POSHs and other MOSHs this MOSH consists of
- source [[URL](https://www.wikidata.org/wiki/Property:P2699)]
  - URL to the 2D model (e.g [technical drawing](https://www.wikidata.org/wiki/Q192521), gerber file) in the original file format
  - qualifiers are defined [here](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-explanatory.md)
  - URL to the [3d model](https://www.wikidata.org/wiki/Property:P4896) in the original file format
  - additional technical documentation
  - as required by TsDC
  - e.g. manufacturing instructions, post-processing specifications (e.g. as MD files)
- [x] standard [[technical standard](https://www.wikidata.org/wiki/Q317623)]
  - standard used/considered in the _design_ (other then DIN SPEC 3105-1)
  - property hopefully changes to [[open standard](https://www.wikidata.org/wiki/Q681263)] in the future :)
- [x] status [[version type](https://www.wikidata.org/wiki/Property:P548)]
  - development status, preferably use defined designations like:
    - development
    - prototype
    - certified
    - in production
- [x] TsDC-ID [[technical standard](https://www.wikidata.org/wiki/Q317623)]/[[open standard](https://www.wikidata.org/wiki/Q681263)]
  - state applying [TsDC-IDs](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-DB-print.md)
- [x] version [[software version identifier](https://www.wikidata.org/wiki/Property:P348)]\
  - = unambiguous reference of the version of the hardware design
    and the version of the documentation
  - **@wikidata**, suggestion:
    - change property title to "project version identifier" as this concept can be (and is) used for non-software projects
    - add qualifiers: software, hardware, okhv
  - e.g. a manually given version number or a commit hash
  - suggestion for the projects: use the [semantic versioning scheme](https://semver.org/)

### manually entered metadata

#### manifest file

##### OSH Module (MOSH)

Which is an **assembly of components (and subassemblies) with clear input, output and interfaces that fully complies with DIN SPEC 3105-1 and this metadata standard**.

- (and thus can be used independently from the rest of the original machine as
  far as required inputs and interfaces are respected);
- metadata shall represent functionality and "position inside the OSH ecosystem" (→ BoM = link to other modules)

**Metadata:**

- okhv
- name
- organisation
- image
- language
- version
- function
- IPC (multiple)
- sBoM
- license / alternative-license
- readme
- certificate
- repo
- standard (multiple)
- functional-metadata (multiple)
- TsDC (multiple)
- source
- export

**COMMENT:** manufacturres, funders, standards etc. would be on the same level as `OSH Module`

##### Piece of OSH (POSH)

Which is a **component or assembly that fully complies with DIN SPEC 3105-1 and this metadata standard**.

- metadata shall enable decentralised production, modification, operation and maintenance
- …and facilitate 'packaging' (=find the files you actually need)

**Metadata:**

- okhv
- name
- image
- version
- standard (multiple)
- TsDC-ID (multiple)
- source (multiple)
- export (multiple)
- production-metadata

##### Standard Component (STD)

Which is a **component or assembly that is officially standardised**.

- name
- standard designation

##### Purchased Component (BUY)

Which is a **component or assembly that is neither officially standardised nor fully compliant with DIN SPEC 3105-1 and hence just bought**.

**Metadata:**

- name
- buy-reference

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

| Pos. | Name         | Units | Type   | Reference                                                           |
|------|--------------|-------|--------|---------------------------------------------------------------------|
| 1    | casing       | 2     | POSH   | link to [POSH file](#piece-of-osh-posh)                             |
| 2    | screw        | 4     | STD    | standard designation                                                |
| 3    | gear box     | 1     | MOSH   | link to [OSH-Module](#osh-module)                                   |
| 4    | Raspberry Pi | 1     | BUY    | unambiguous reference (not standardised)                            |
| 5    | holder       | 1     | POSH   | link to [POSH file](#piece-of-osh-posh)                             |
| 5.1  | bracket      | 2     | POSH   | link to [POSH file](#piece-of-osh-posh)                             |
| 5.2  | screw        | 2     | STD    | standard designation                                                |
| 5.3  | arm          | 2     | POSH   | link to [POSH file](#piece-of-osh-posh)                             |
| 6    | controller   | 1     | MOSH   | link to link to [OSH-Module](#osh-module)                           |

### metadata added by parser

- file-format
  - to be parsed from source & export URLs (`source-2d`, `source-3d`, `source+`, `export-2d`, `export-3d`, `export+`)
- status
  - to be assessed judging from version (0.x.x; beta) or source URL (dev branch) or the presence of an attestation URL
- fork-of
  - information from the GitHub/Gitlab API ('fork of' etc.)
  - if no API available: assessment based on version, URL, presence of other _very_ similar OSH in the knowledge base (judging e.g. from 'consists of')
- assign classes to instances
  - by sBoM `Types` column

## data structure

MOSH has

- own metadata
- POSH, STD, BUY
  - each with quantities
