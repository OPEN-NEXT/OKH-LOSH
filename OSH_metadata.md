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

#### A OSHM file

1. is named `.okh`\
  (note the dot\
  …so the file won't get changed unintentionally & it will be hidden on Linux-based systems which gives a neater look & it's easier for the crawler to identify these files);
2. is located in the root directory of the [OSH Module](#osh-module-oshm).

#### A POSH file

1. is named `.okh-<anything>`\
  while `<anything>` is replaced by any type of identifier (e.g. a short name)\
  (note the dot);
2. should be stored in reasonable ways (e.g. in the folder containing the design files)
  for a intuitive repo structure (e.g. so   people get also the metadata file when they clone just this component).\
  However as files are unambiguously referenced in the OSHM file you can place them wherever you like.

### File Formats

To connect your OSH to the OSHI, your metadata must be stored in one of the following formats:

- [JSON-LD](https://json-ld.org/)
- YAML (for OKHv1 **only**)
- We may allow more file formats in the future as everything is converted and uploaded to the Wikibase instance anyway.

Please use the linked templates to enter your data.

Background:\
The crawler will take this metadata as basic input, add additional information to it (e.g. from the Gitlab API) and build a TTL file with all that information which is then integrated in Wikibase.
You see, it doesn't really matter in which file format you'll save your metadata as long as the crawler is able to interpret it.

## Ontology

Mostly Wikidata's ontology, which is based on [OWL 2](https://www.w3.org/TR/owl2-rdf-based-semantics/)

We'll use Wikidata's terms:

- xx = classes
- properties = slots
- qualifiers = xx

### Classes & Slots

#### Classes

- class [[class](https://www.wikidata.org/wiki/Property:P2308)]
  - [OSHM](#osh-module-oshm)
  - [POSH](#piece-of-osh-posh)
  - STD – standard component
  - BUY – purchased component

#### Slots/Properties [data type]

- alternative-license [[reference URL](https://www.wikidata.org/wiki/Property:P854)]
  - **@wikidata**, suggestion:
    - add as new qualifier: alternative-license
  - URL to legal code of the license (e.g. LICENSE.md) in case SPDX identifier is not existent
- attestation [[reference URL](https://www.wikidata.org/wiki/Property:P854)]
  - link to certificate (OSHWA, FSF, DIN SPEC 3105)
  - **@wikidata**, suggestion:
    - add as new qualifiers: certificate, attestation
  - buy-reference [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)]
  - **@wikidata**, suggestion:
    - add as new property: buy-reference
  - unambiguous reference for non-standard purchased components
  - others shall be able to identify/procure this component only by the given reference(s)
- export-2d [[URL](https://www.wikidata.org/wiki/Property:P2699)]
  - **@wikidata**, suggestion:
    - add as new qualifier: export-2D
  - URL to the exported 2D model (e.g [technical drawing](https://www.wikidata.org/wiki/Q192521), gerber file etc.)
  - e.g. PDF files
- export-3d [[URL](https://www.wikidata.org/wiki/Property:P2699)]
  - **@wikidata**, suggestion:
    - add as new qualifier: export-3D
  - URL to the exported [3d model](https://www.wikidata.org/wiki/Property:P4896)
  - e.g. STEP, STL
- export+ [[URL](https://www.wikidata.org/wiki/Property:P2699)]
  - **@wikidata**, suggestion:
    - add as new qualifier: export+
  - URL to complementary documents (e.g. manufacturing instructions)
  - e.g. PDF files
- file-format [[file format](https://www.wikidata.org/wiki/Property:P2701)]
- fork-of [[fork](https://www.wikidata.org/wiki/Q332903)]
  - **@wikidata**, suggestion:
    - open description for non-software project as forks exist also for documents and hardware
    - specify source project this project has been forked from
- function [[scope and content](https://www.wikidata.org/wiki/Property:P7535)]\
  - **@wikidata** any better idea/better matching property available?
  - functional description, e.g. what it actually does, what problem it solves, for whom, under which conditions etc.
  - so if you whish that someone finds & uses your OSHM specifically e.g. for COVID-19-crisis response, include relevant keywords in this field
  - optional: description of input, output and interfaces
- functional-metadata [[supported metadata](https://www.wikidata.org/wiki/Property:P8203)]
  - _very_ technology-specific, not to be standardised here
  - dimensions
  - material
  - weight
  - RPM
  - …
- image [[Commons compatible image available at URL](https://www.wikidata.org/wiki/Property:P4765)]
  - URL to a meaningful picture of this module
- IPC [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)]
  - **@wikidata**, suggestion:
    - add as new property: IPC-identifier
  - international, stable category system for projects in the patent domain (as OSH)
- language [[IETF language tag](https://www.wikidata.org/wiki/Property:P305)]
  - tag for the language in which the documentation is available
    using IETF language tags
    following the BCP 47 standard),
    such as `en` or `en-GB`
- license [[SPDX license identifier](https://www.wikidata.org/wiki/Property:P2479)]
- name [[name](https://www.wikidata.org/wiki/Property:P2561)]\
- **@wikidata** any better idea/more precise property available?
  - working title
  - designation for POSH, standard or purchased component
- okhv [[software version identifier](https://www.wikidata.org/wiki/Property:P348)]\
  - = version of the metadata standard used in this file
  - **@wikidata**, suggestion:
    - change property title to "project version identifier" as this concept can be (and is) used for non-software projects
    - add qualifiers: software, hardware, okhv
- owner [[copyright holder](https://www.wikidata.org/wiki/Property:P3931)]
  - organisation/individual behind the hardware design
- parent-asm [[part of](https://www.wikidata.org/wiki/Property:P361)]
  - identifies the subassembly (NOT the [OSHM](#osh-module-oshm)) this component is part of
- production-metadata [[supported metadata](https://www.wikidata.org/wiki/Property:P8203)]
  - yet to be specified
  - outer dimensions (dimension + (measuere type+)measures e.g. mm-ø20x100 for a cylindric thing)
    - cuboid (mm-100x50x20)
    - cylinder (mm-ø50x100)
    - sphere (mm-ø15)
  - smallest tolerance
    - preferrably use designation according to ISO 286-1:2010
  - finest surface roughness in µm
  - material
  - manufacturing technology (machining, additive, forming, casting,…)
- quantity [quantity](https://www.wikidata.org/wiki/Property:P1114)
  - quantity of a component in the `parent-asm`
- readme [[URL](https://www.wikidata.org/wiki/Property:P2699)]
  - **@wikidata**, suggestion:
    - add as new qualifier: readme
  - link to general project description; may be the project webpage, may be the README.md
- repo [[URL](https://www.wikidata.org/wiki/Property:P2699)]
  - **@wikidata**, suggestion:
    - add as new qualifier: repository
  - URL to development channel
  - people will use the URL to contribute in any way (reporting issues, giving feedback, joining the development)
- sBoM [[URL](https://www.wikidata.org/wiki/Property:P2699)]
  - **@wikidata**, suggestion:
    - add as new qualifier: sBoM
  - links to a CSV containing all POSHS and other OSHMs this OSHM consists of
- source-2d [[URL](https://www.wikidata.org/wiki/Property:P2699)]
  - **@wikidata**, suggestion:
    - add as new qualifier: source-2D
  - URL to the 2D model (e.g [technical drawing](https://www.wikidata.org/wiki/Q192521), gerber file) in the original file format
- source-3d [[URL](https://www.wikidata.org/wiki/Property:P2699)]
  - **@wikidata**, suggestion:
    - add as new qualifier: source-3D
  - URL to the [3d model](https://www.wikidata.org/wiki/Property:P4896) in the original file format
- source+ [[URL](https://www.wikidata.org/wiki/Property:P2699)]
  - **@wikidata**, suggestion:
    - add as new qualifier: source+
  - additional technical documentation
  - as required by TsDC
  - e.g. manufacturing instructions, post-processing specifications (e.g. as MD files)
- standard [[technical standard](https://www.wikidata.org/wiki/Q317623)]
  - standard used/considered in the _design_ (other then DIN SPEC 3105-1)
  - property hopefully changes to [[open standard](https://www.wikidata.org/wiki/Q681263)] in the future :)
- standard-designation [[External Identifier](https://www.wikidata.org/wiki/Wikidata:External_identifiers)]
  - **@wikidata**, suggestion:
    - add as new property: standard-designation
  - unambiguous reference for a standard component (preferably naming the latest standard)
  - connection point for the future library of standard components (→ automatic checking for unambiguous referencing)
- status [[version type](https://www.wikidata.org/wiki/Property:P548)]
  - development status, preferably use defined designations like:
    - development
    - prototype
    - certified
    - in production
- TsDC-ID [[technical standard](https://www.wikidata.org/wiki/Q317623)]/[[open standard](https://www.wikidata.org/wiki/Q681263)]
  - **@wikidata**, suggestion:
    - add as new qualifier: TsDC-ID
  - state applying [TsDC-IDs](https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/TsDC-DB-print.md)
- version [[software version identifier](https://www.wikidata.org/wiki/Property:P348)]\
  - = unambiguous reference of the version of the hardware design
    and the version of the documentation
  - **@wikidata**, suggestion:
    - change property title to "project version identifier" as this concept can be (and is) used for non-software projects
    - add qualifiers: software, hardware, okhv
  - e.g. a manually given version number or a commit hash
  - suggestion for the projects: use the [semantic versioning scheme](https://semver.org/)

### manually entered metadata

#### manifest file

##### OSH Module (OSHM)

**Intro:**

- = assembly of components (and subassemblies) with clear input, output and interfaces
  - (and thus can be used independently from the rest of the original machine as far as required inputs and interfaces are respected);
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
- source-3d
- source-2d
- source+
- export-3d
- export-2d
- export+

**COMMENT:** manufacturres, funders, standards etc. would be on the same level as `OSH Module`

##### Piece of OSH (POSH)

**Intro:**

- = component or assembly of components
- metadata shall enable decentralised production, modification, operation and maintenance
- …and facilitate 'packaging' (=find the files you actually need)

**Metadata:**

- okhv
- name
- image
- version
- standard (multiple)
- TsDC-ID (multiple)
- source-3d (multiple)
- source-2d (multiple)
- source+ (multiple)
- export-3d (multiple)
- export-2d (multiple)
- export+ (multiple)
- production-metadata

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
| 1    | casing       | 2     | POSH   | link to [POSH file](#piece-of-osh-posh)|
| 2    | screw        | 4     | STD   | standard designation                                                                |
| 3    | gear box     | 1     | OSHM     | link to [OSH-Module](#osh-module)                                                   |
| 4    | Raspberry Pi | 1     | BUY  | unambiguous reference (not standardised)                                            |
| 5    | holder       | 1     | POSH | link to [POSH file](#piece-of-osh-posh)|
| 5.1  | bracket      | 2     | POSH   | link to [POSH file](#piece-of-osh-posh)|
| 5.2  | screw        | 2     | STD   | standard designation                                                                |
| 5.3  | arm          | 2     | POSH   | link to [POSH file](#piece-of-osh-posh)|
| 6    | controller   | 1     | OSHM      | link to link to [OSH-Module](#osh-module)|

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
