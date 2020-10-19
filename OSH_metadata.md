# Representative metadata for OSH

## Intro

new intro needed

## Scope

_This_ draft shall support the following user groups:

1. developers
   - first and foremost facilitate **design reuse**
   - replace manual packaging; metadata shall enable a download button for: <!--- resource to check: <https://github.com/kanzure/skdb> (**apt-get for hardware**) -->
     - production files (export only)
     - developer files (sources only)
     - full package (export + sources)
2. manufacturers / service providers
   - find OSH ready for decentralised (mass) production, maintenance and service provision
3. researchers

### General requirements

- no unnecessary effort for metadata providers (developers etc.)\
  → use data from APIs or automated interpretation where possible/feasible

## Basic structure

- information is provided in manifest files
- OSH platforms that offer an open API with data fields compatible to this draft can be connected to our crawler. It will pull the API and enter the data directly into the knowledge base.
- a MOSH is represented by its manifest file, linking to a sBoM
  - the sBoM refrences all components of this MOSH e.g. linking to the manifest files of POSHs

### Glossary

- manifest file – file in a repository containing metadata for a [MOSH](#osh-module-MOSH) or [POSH](#piece-of-osh-posh)
- simplified BoM (sBoM) – CSV giving the references of all components of a MOSH
- Types of components:
  - [MOSH](#osh-module-MOSH) – module distributed as open source hardware
  - [POSH](#piece-of-osh-posh) – part distributed as open source hardware
  - STD – standard component
  - BUY – purchased component

#### manifest file

A manifest file is a file in a repository containing metadata for a [MOSH](#osh-module-MOSH) or [POSH](#piece-of-osh-posh).

It shall use the **JSON** file format.
Please use the linked templates to enter your data.\
We may allow more file formats in the future.

Background:\
The crawler will take this metadata as basic input, add additional information
to it (e.g. from the Gitlab API), build a JSON-LD file with all that information
and uploads it to Wikibase via an open API. Technically it doesn't really matter
in which file format you'll save your metadata as long as the crawler is able to
interpret it.

##### OSH Module (MOSH)

Which is an **assembly of components (and subassemblies) with clear input, output and interfaces that fully complies with DIN SPEC 3105-1 and this metadata standard**.

- (and thus can be used independently from the rest of the original machine as
  far as required inputs and interfaces are respected);
- metadata shall represent functionality and "position inside the OSH ecosystem" (→ BoM = link to other modules)

**Metadata:**

- okhv
- name
- image (multiple)
- language
- version
- forkOf
- function
- IPC (multiple)
- sBoM
- license / alternative-license
- readme
- certificate (multiple)
- repo
- standard (multiple)
- functional-metadata (multiple)
- source
- export

**A MOSH file:**

1. is named `.okh`\
  (note the dot\
   …so the file won't get changed unintentionally & it will be hidden on
   Linux-based systems which gives a neater look & it's easier for the crawler
   to identify these files);
2. is located in the root directory

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
- source (multiple)
- export (multiple)
- production-metadata (multiple)

**A POSH file:**

1. is named `.okh-<anything>`\
  while `<anything>` is replaced by any type of identifier (e.g. a short name)\
  (note the dot);
2. should be stored in reasonable ways (e.g. in the folder containing the design files)
  for a intuitive repo structure (e.g. so   people get also the metadata file when they clone just this component).\
  However as files are unambiguously referenced in the MOSH file you can place them wherever you like.

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

## Ontology

This draft mostly relies on Wikidata's ontology, which is based on
[OWL 2](https://www.w3.org/TR/owl2-rdf-based-semantics/).

As a consequence we also use Wikidata's terms:

| Wikidata term | term in other resources |
| --- | --- |
| class | class |
| property | slot/feature/attribute |
| qualifier | facet |
| itemt | instance |

This document in the following will only describe how the ontology works and why it looks as it does.
Find the actual ontology [here](osh-metadata.ttl).

### Competency questions / use cases

<!--- add: which queries adress these questions, list related properties in queries -->

**NOTE:** Queries aiming to cover the following use cases are referenced (& linked) in square brackets.

1. explore this knowledge base [[I]](#i-information-queries)
   - view all information of a MOSH or POSH available in this knowledge base [[i01]](#i01-available-information)
   - …
2. a powerful filter for OSH [[F]](#f-filter-queries)
   - find OSH in a specific field of technology [[f01]](#f01-technology-field)
   - find OSH for a specific use case (including technical standards, certificates, development stage) [[f02]](#f02-use-case)
     - Option 1: filter for specific technology fields
     - Option 2: find OSH that does allow proprietary adoptions
   - filter for languages [[f03]](#f03-language)
   - find versions & variants/forks of a certain component or module [[f04]](#f04-variants)
3. automated assessments [[A]](#a-assessment-queries)
   - license compatibility [[a01]](#a01-license-compatibility)
     - Option 1: with OSHWA
     - Option 2: between 2 given MOSHs
   - documentation complete according to DIN SPEC 3105-1? [[a02]](#a02-documentation)
   - Are source files editable with the software I already have? [[a03]](#a03-file-formats)
     - Variant 1: list all file formats used for source material
     - Variant 2: compare a list from Variant 1 with list of supported file formats of selected software calling a sublibrary
     - Options for both variants:
       - Option 1: without submodules
       - Option 2: including all submodules
   - How widespread is the use of a specific component (MOSH/POSH/STD/BUY) [[a04]](#a04-dissemination)
     - Option 1: …in a certain field of technology?
     - Option 2: add a list of all MOSHs using the selected component
4. packaging [[P]](#p-packaging-queries)
   - full package [[p01]](#p01-full-package)
   - source package [[p02]](#p03-export-package)
   - export package [[p03]](#p03-export-package)
5. support research on OSH (see wp2-dashboard) [[R]](#r-research-queries)
   - how many contributors?
   - where are contributors located? (= is there any project closeby?)
   - what projects contributors contribute to?
   - dynamics: who contributes, reports/solves issues etc.?

### component relations

parsing the `sBoM`:

- `name`
- `quantity`
- `parentASM`
- MOSH
  - `moduleReference`
    - pull data from corresponding manifest file (name, version, … , source & export), again with a `sBoM` etc.
- POSH
  - `pieceReference`
    - pull data from corresponding manifest file (name, version, … , source & export)
- STD
  - `stdReference`
- BUY
  - `buyReference`

### Standard queries

**NOTE:** As some data fields/properties have multiple uses the following list will obviously contain duplicate mentions of properties.

For details of the properties see descriptions in the [ontology](osh-metadata.ttl).

#### [I] information queries

##### i01 available information

return all data fields of a specific MOSH or POSH

#### [F] filter queries

##### f01 technology field

- find or exclude MOSHs with specific `patentClass` (multiple)

##### f02 use case

for MOSHs:

- search for keywords in `function` (free text)
- filter for specific
  - `standard`
  - `status`
  - `attestation` (boolean: is-empty)
  - `certificate` (boolean: is-empty)
- Option 1: filter for specific `patentClass`
- Option 2: filter for copyleft-categories of licenses by calling a sub-library with `spdxLicense`

##### f03 language

- find or exclude MOSHs with specific IETF language tag (`language`) (multiple)

##### f04 variants

- find forks (`forkOf`) or different versions (`version`) of a MOSH or POSH

#### [A] assessment queries

##### a01 license compatibility

- Option 1: compare `spdxLicense` of a specific MOSH with a list of OSHWA-compliant licenses calling a sub-library

- Option 2: check compatibility of licenses of specific MOSHs by calling a sub-library with `spdxLicense`

##### a02 documentation

- check whether or not [full packaging](#p01-full-package) would include entries for
  - `okhv`
  - `name`
  - `repository`
  - `version`
  - `owner`
  - `spdxLicense`
    - while checking for [OSHWA-compliance](#a01-license-compatibility)
  - `function`
  - design files (hence a `sBoM` is a prerequisiste)
    - `name`
    - `quantity`
    - for MOSHs included
      - `source`
      - `export`
    - for POSHs included
      - `source`
      - `export`
    - for STDs included
      - `stdReference`
    - for BUYs included
      - `buyReference`
- returns a boolean ("probably complete", "probably uncomplete")
  - add a report of what's missing in case one ore more of the mentioned data fields are empty

##### a03 file formats

for MOSHs:

- Variant 1:
  - return list of all `fileFormat` used in `source`
- Variant 2:
  - user input is a selection of software
  - get list of supported file formats of selected software from sub-library
  - check whether files linked as `source` contain a `fileFormat` that is _not_ part of this list
  - return boolean
    - add a list of POSHs/MOSHs including a unsupported `fileFormat` indicating the corresponding file (tree-like list)
- options for both variants:
  - Option 1: exclude the `source` of submodules
  - Option 2: include the `source` of submodules

##### a04 dissemination

- get number of MOSHs that include a seleted component MOSH/POSH/STD/BUY in their `sBoM`
- Option 1: split number by `patentClass` of the MOSHs using the selected component
- Option 2: add a list (`name`, `version` and internal wikibase-link to the MOSHs using the selected component)

#### [P] packaging queries

#### p01 full package

A package of a certain MOSH includes the following.

NOTE 1: The query may give the option to load submodules (other included MOSHs) or just link to them. In case of loading them, naturally the same requirements apply as for any other MOSH.

NOTE 2: Packages may be (most likely) incomplete. Empty fields are gaps in the resulting package.

- general information
  - get version of metadata standard used
    - `okhv`
  - identification
    - `name`
    - `repository`
    - `version`
    - `forkOf`
    - `language`
  - legal
    - `owner`
    - `spdxLicense`
    - `alternativeLicense`
  - development stage
    - `status`
    - `attestation`
    - `certificate`
  - basic description
    - `patentClass`
    - `standard`
    - `function`
    - `readme`
    - `image`
    - `functionalMetadata`
    - `productionMetadata`
- design files (=tree with links/references)
  - `name`
  - `quantity`
  - MOSH (submodules)
    - `repository` & `version` when just referencing submodules
    - full package when loading submodules
  - POSH
    - `okhv`
    - `version`
    - `standard`
    - `image`
    - `productionMetadata`
    - `source`
    - `export`
  - STD
    - `stdReference`
  - BUY
    - `buyReference`

#### p02 source package

= [p01 full package](#p01-full-package) without `export` fields

#### p03 export package

= [p01 full package](#p01-full-package) without `source` fields

#### [R] research queries
