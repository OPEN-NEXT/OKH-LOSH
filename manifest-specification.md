---
title: Specification on Manifest files
# These two are supplied their final value from `git describe`
subtitle: OKHv2.0
lang: en-UK
charset: UTF-8
papersize: a4
geometry: "top=2cm,bottom=2cm,left=3cm,right=3cm"
description: >
  xxx
---

# Intro

# Manifest Types

## MOSH

## POSH

## sBoM

# General Conventions

## File Path Convention

For file referencing we allow 3 types of paths: relative, absolute and an URL.

### Relative Path

A relative path starts from some directory the corresponding manifest file is located in.
The file reference _never_ starts with an "`/`"

**EXAMPLE**

Given the following folder structure:

`/3DParts/ClampRing`

manifest and source file of the POSH `Clamp Ring` are located in the same folder;
the file reference would be simply:

`clampring.scad`

Given the alternative folder structure:

`/3DParts/ClampRing/source`

where manifest and other additional files are located in `/3DParts/ClampRing` whereby the source lies in in the subfolder `source`, the file reference would be:

`source/clampring.scad`

### Absolute Path

An absolute path always starts from the root directory (= repository folder).
The file reference _always_ starts with an "`/`"

**EXAMPLE**

`/3DParts/ClampRing/ClampRing.scad`

### URL

placeholder

## Redundant Data

Redundant data can be omitted.
The crawler will then take the data from the next higher level.

**EXAMPLE**

A MOSH file states

`spdx-license = "CERN-OHL-S-2.0	"`

If a POSH in the same repository has the same license (which is most likely the case),
there's no need to state the license _also_ in the manifest file for this POSH.
The crawler will then assume the MOSH-entry.

# Data Fields

## MOSH Fields

## POSH Fields

## sBoM Fields

### Position Number

### Name

### Quantity

### Type

### Reference

Unambiguous reference of the listed component.
By [Type](#type) the following qualify as entries:

- MOSH (from another repository): URL to release or snapshot of the used version (e.g. specific git commit)
- POSH: relative or absolute link