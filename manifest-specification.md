---
title: Specification on Manifest files
subtitle: OKHv2.0.0
lang: en-UK
charset: UTF-8
papersize: a4
geometry: "top=2cm,bottom=2cm,left=3cm,right=3cm"
description: >
  TODO
---

# Intro

# Manifest Types

## MOSH

- version of a MOSH is specified by the version tag in the repository

## POSH

## sBoM

# General Conventions

## File Path Convention

For file referencing we allow 3 types of paths: relative, absolute and an URL.

### Relative Path

A relative path starts from some directory
the corresponding manifest file is located in.
The file reference _never_ starts with a "`/`"

#### EXAMPLE {#relative-path-example}

Given the following folder structure:

`/3DParts/ClampRing`

manifest and source file of the POSH `Clamp Ring` are located in the same folder;
the file reference would be simply:

`clampring.scad`

Given the alternative folder structure:

`/3DParts/ClampRing/source`

where manifest and other additional files are located in `/3DParts/ClampRing`
whereby the source lies in in the subfolder `source`,
the file reference would be:

`source/clampring.scad`

### Absolute Path

An absolute path always starts from the root directory (= repository folder).
The file reference _always_ starts with an "`/`"

#### EXAMPLE {#absolute-path-example}

`/3DParts/ClampRing/ClampRing.scad`

### URL

placeholder

# Downward Compatibility

We will continue to support [OKHv1.0.0](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1)
YAML files.\
However, we strongly recommend to update to the current manifest specification.

## Redundant Data

Redundant data can be omitted.
The crawler will then take the data from the next higher level.

#### EXAMPLE {#redundant-data-example}

A MOSH file states

`license = "CERN-OHL-S-2.0"`

If a POSH in the same repository has the same license (which is most likely the case),
there's no need to state the license _also_ in the manifest file for this POSH.
The crawler will then assume the MOSH-entry.

# Data Fields

## MOSH Fields

### license

- string
- SPDX-ID of the license
- short title of the license otherwise (alternative license)

Entry is checked against the current machine readable list of SPDX licenses.

If the entry is

- found: `license = okh:spdxLicense`
- not found: `license = okh:alternativeLicense`

## POSH Fields

## sBoM Fields

### Position Number

### Name

### Quantity

### Type

### Reference

Unambiguous reference of the listed component.
By [Type](#type) the following qualify as entries:

- MOSH (from another repository):
  - commit-specific URL to manifest file for this MOSH
  - URL to release or snapshot of the used version (e.g. specific git commit)
  - bad but possible: just URL to MOSH repo
    → will point to versionless representation in the DB (if any)
  - very bad: just a name
- POSH: manifest file for this POSH
- STD: standard designation
- BUY: any unambiguous reference for this proprietary component
  (preferably not just an URL, those links may die)
