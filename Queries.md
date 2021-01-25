# Description of standard queries

**NOTE:** For details of the properties see descriptions in the [ontology](osh-metadata.ttl).

## [I] information queries

### i01 available information

return all data fields of a specific MOSH

## [F] filter queries

### f01 technology field

- find or exclude MOSHs with specific `patentClass` (multiple)

### f02 use case

for MOSHs:

- search for keywords in `function` (free text)
- filter for specific
  - `standard`
  - `projectStage`
  - `attestation` (boolean: is-empty)
  - `certificate` (boolean: is-empty)
- Option 1: filter for specific `patentClass` &/ `tsdcID`
- Option 2: filter for copyleft-categories of licenses by calling a sub-library with `spdxLicense`

### f03 language

- find or exclude MOSHs with specific IETF language tag (`language`) (multiple)

### f04 variants

- return versions and forks of a MOSH

## [A] assessment queries

### a01 license compatibility

- Option 1: compare `spdxLicense` of a specific MOSH with a list of OSHWA-compliant licenses calling a sub-library

- Option 2: check compatibility of licenses of specific MOSHs by calling a sub-library with `spdxLicense`

### a02 documentation

<!-- ToDO: change to → return available documentation references --->

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

### a03 file formats

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

### a04 dissemination

- get number of MOSHs that include a seleted component MOSH/POSH/STD/BUY in their `sBoM`
- Option 1: split number by `patentClass` of the MOSHs using the selected component
- Option 2: add a list (`name`, `version` and internal wikibase-link to the MOSHs using the selected component)

## [P] packaging queries

## p01 full package

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

## p02 source package

= [p01 full package](#p01-full-package) without `export` fields

## p03 export package

= [p01 full package](#p01-full-package) without `source` fields

## [R] research queries
