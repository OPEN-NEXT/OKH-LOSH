# Representative metadata for OSH

<!--
About *table of contents* (TOC)

NOTE:
For each in-document command,
make sure that there is a blank line before and after.

Support in different Markdown software:

* CodiMD, HedgeDoc & other web based Markdown tools
  support the in-document `[TOC]` command
* GitLab supports the in-document `[[_TOC_]]` command
* Kramdoc supports the in-document `{:toc max_level=3 }` command
* GitHub does not support anything,
  see https://github.com/isaacs/github/issues/215#issuecomment-561605313
* pandoc supports the `\-\-toc` command-line flag,
  which will put a TOC on the start of the document
-->

[TOC]

[[_TOC_]]

## Intro

TODO new intro neededs

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

- Information is provided via platform APIs. The crawler will call these APIs and collect the data in JSON files.
  - in case of GitHub/GitLab some information is provided in the API, some shall be provided in manually created [manifest files](#manifest-file), see [GitHub-Table](#github) for details
  - those manifest files can be searched via the GitHub-API (see [#24](https://github.com/OPEN-NEXT/LOSH/issues/24) for details)
- The crawler's JSON files are translated into JSON-LD and submits it to the Wikibase-API
- a MOSH is represented by its manifest file, linking to a sBoM
  - the sBoM refrences all components of this MOSH: included POSHs, standard and proprietary components

### Glossary

- manifest file – file in a repository containing metadata for a [MOSH](#osh-module-MOSH)
- simplified BoM (sBoM) – CSV giving the references of all components of a MOSH
- Types of components:
  - [MOSH](#osh-module-MOSH) – module distributed as open source hardware
  - [POSH](#piece-of-osh-posh) – part distributed as open source hardware
  - STD – standard component
  - BUY – purchased component

### Elements, Locations & Naming

#### manifest file

A manifest file is a file in a repository containing metadata for a [MOSH](#osh-module-MOSH).

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

**A MOSH file:**

1. is named `.okh.json`\
  (note the dot\
   …so the file won't get changed unintentionally & it will be hidden on
   Linux-based systems which gives a neater look & it's easier for the crawler
   to identify these files);
2. is located in the root directory

##### Piece of OSH (POSH)

Which is a **component or assembly that fully complies with DIN SPEC 3105-1 and this metadata standard**.

- metadata shall enable decentralised production, modification, operation and maintenance
- …and facilitate 'packaging' (=find the files you actually need)

**A POSH:**

is located in an individual folder that only includes data related to this POSH, specifically source & export files.

This folder is linked in the sBoM.

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
  - column `Reference` includes single entries only
- subassemblies are _not_ represented as individual modules, but included via structured pos. numbers

**Referencing:**

MOSH

- URL to used _release_
  - if release information is not available (e.g. because it's a messy repository), use any kind of permalink instead e.g. linking to the last commit that was made before you used the design files

POSH

- URLs to a [POSH](#piece-of-osh-posh) (= it's corresponding folder)

STD

- standard designation\
  e.g. "hexagon screw ISO 4017 – M12 × 80 – 8.8"

BUY

- unambiguous reference to purchased part (which can be either URLs or designations)\
  e.g. "100k, R_0603_1608" for a resistor

**Location and Naming Convention:**

- to be stored as CSV in the same level as the metadata file linking to this sBoM
- name *must* contain `sBoM`

**EXAMPLE:**

| Pos. | Name         | Units | Type   | Reference                                                           |
|------|--------------|-------|--------|---------------------------------------------------------------------|
| 1    | casing       | 2     | POSH   | link to [POSH](#piece-of-osh-posh) folder                           |
| 2    | screw        | 4     | STD    | standard designation                                                |
| 3    | gear box     | 1     | MOSH   | link to _release_ of this [MOSH](#osh-module-mosh)                  |
| 4    | Raspberry Pi | 1     | BUY    | unambiguous reference (not standardised)                            |
| 5    | holder       | 1     | POSH   | link to [POSH](#piece-of-osh-posh) folder                           |
| 5.1  | bracket      | 2     | POSH   | link to [POSH](#piece-of-osh-posh) folder                           |
| 5.2  | screw        | 2     | STD    | standard designation                                                |
| 5.3  | arm          | 2     | POSH   | link to [POSH](#piece-of-osh-posh) folder                           |
| 6    | controller   | 1     | MOSH   | link to _release_ of this [MOSH](#osh-module-mosh)                  |

## Required Metadata

Requirements are platform-specific,
since different entries can be automatically filled via their API -
so people don't need to provide manual entries.

### GitHub

|JSON key|RDF type|MOSH-manual|MOSH-API|
|---|---|---|---|
|`okh-version`|`okh:okhv`|x||
|`image` (multiple)|`okh:image`|x||
|`documentation-language`|`okh:documentationLanguage`|x||
|`function`|`okh:function`|x||
|`patent-class` (multiple)|`okh:patentClass`|x||
|`tsdc-id` (multiple)|`okh:tsdcID`|x||
|`simplified-bom`|`okh:sBoM`|x||
|`certificate` (multiple)|`okh:certificate`|x||
|`standard` (multiple)|`okh:standard`|x||
|`functional-metadata` (multiple)|`okh:functionalMetadata`|x||
|`production-metadata` (multiple)|`okh:productionMetadata`|x||
|`assembly-instruction` (multiple)|`okh:assemblyInstruction`|x||
|`version`|`okh:version`||x|
|`fork-of`|`okh:forkOf`||x|
|`license` / `alternative-license`|`okh:license` / `okh:alternativeLicense`||x|
|`readme`|`okh:readme`||x|
|`repo`|`okh:repository`||x|

The *JSON key* column in the table above,
corresponds to the keys in `.okh.json`.

## Ontology

This draft mostly relies on Wikidata's ontology, which is based on
[OWL 2](https://www.w3.org/TR/owl2-rdf-based-semantics/).

As a consequence we also use Wikidata's terms:

| Wikidata term | term in other resources |
| --- | --- |
| class | class |
| property | slot/feature/attribute |
| qualifier | facet |
| item | instance |

This document in the following will only describe how the ontology works and why it looks as it does.
Find the actual ontology [here](osh-metadata.ttl).

### Competency questions / use cases

**NOTE:** Queries aiming to cover the following use cases are referenced (& linked) in square brackets.

1. explore this knowledge base [[I]](#i-information-queries)
   - view all information of a MOSH available in this knowledge base [[i01]](#i01-available-information)
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

<!--- rework references as they have been removed in [#37](https://github.com/OPEN-NEXT/LOSH/issues/37) --->

parsing the `sBoM`:

- `name`
- `quantity`
- `parentASM`
- MOSH
  - `moduleReference`
    - pull data from corresponding MOSH file (name, version, … , source & export), again with a `sBoM` etc.
- POSH
  - `pieceReference`
    - pull data from corresponding POSH (name, source & export)
- STD
  - `stdReference`
- BUY
  - `buyReference`

### Standard queries

**NOTE:** As some data fields/properties have multiple uses the following list will obviously contain duplicate mentions of properties.

For details of the properties see descriptions in the [ontology](osh-metadata.ttl).

#### [I] information queries

##### i01 available information

return all data fields of a specific MOSH

#### [F] filter queries

##### f01 technology field

- find or exclude MOSHs with specific `patentClass` (multiple)

##### f02 use case

for MOSHs:

- search for keywords in `function` (free text)
- filter for specific
  - `standard`
  - `developmentStage`
  - `attestation` (boolean: is-empty)
  - `certificate` (boolean: is-empty)
- Option 1: filter for specific `patentClass` &/ `tsdcID`
- Option 2: filter for copyleft-categories of licenses by calling a sub-library with `spdxLicense`

##### f03 language

- find or exclude MOSHs with specific IETF language tag (`language`) (multiple)

##### f04 variants

- find forks (`forkOf`) or different versions (`version`) of a MOSH

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
  - `licensor`
  - `spdxLicense`
    - while checking for [OSHWA-compliance](#a01-license-compatibility)
  - `function`
  - `tsdcID`
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
    - `licensor`
    - `spdxLicense`
    - `alternativeLicense`
  - development stage
    - `developmentStage`
    - `attestation`
    - `certificate`
  - basic description
    - `patentClass`
    - `tsdcID`
    - `standard`
    - `function`
    - `readme`
    - `image`
    - `functionalMetadata`
    - `productionMetadata`
- design files (=tree with links/references)
  - `name`
  - `quantity`
  - additionally:
    - MOSH (submodules)
      - `repository` & `version` when just referencing submodules
      - full package when loading submodules
    - POSH
      - `source`
      - `export`
    - STD
      - `stdReference`
    - BUY
      - `buyReference`

<!--- MOSH should be referenced as a release! not via repository & version -->

#### p02 source package

= [p01 full package](#p01-full-package) without `export` fields

#### p03 export package

= [p01 full package](#p01-full-package) without `source` fields

#### [R] research queries
