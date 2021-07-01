---
title: Open Know-How Specification for the Library of Open Source Hardware
subtitle: OKH-LOSH
lang: en-UK
charset: UTF-8
papersize: a4
geometry: "top=2cm,bottom=2cm,left=3cm,right=3cm"
SPDX-License-Identifier: GPL-3.0-or-later
...

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

<!---
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

-->




# Intro

This is a fork of the [Open Know-How Specification v1.0.0](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#75fb9df0-a7b3-427f-993a-b23fe1c81a58).
However, lots of changes have been made so it's hard to still call this a fork.
After validation this will be proposed to maintainers of the Open Know-How Specification as a new major version of the specification.

**NOTE:** When we talk about "OSH module" we mean the content of a repository.
Open source hardware (OSH) aims to be modular.
Hence it makes a lot of sense to publish each module in an individual repository
(instead of the whole machine in one large repository).
A module is an assembly of various parts that fulfils a certain purpose.
However, there are exceptions, as a standalone 3D-printed part in a git repository could also fulfil a purpose and qualify as a module.

## Scope

This draft for representative metadata for open source hardware (OSH) shall support the following user groups:

1. developers (specifically to facilitate **design reuse** and to improve discoverability of hardware)
2. makers & manufacturers (find production-ready OSH)
3. researchers (get a quick overview of the current state of OSH developments)

This draft follows a Linked Open Data approach:

- it's a distributed database; projects and platforms hold their own data; LOSH only collects, connects and displays the data
- data processing is based on RDF (data from manifest files (TOML) and platform APIs (JSON) is translated into RDF by the crawler)
- everything is published under free/open licenses; find the RDF [here](), the crawler [here](), LOSH website [here] and the specification (that you are reading) [here]().

This draft aims to facilitate compliance with DIN SPEC 3105-1.

## Basic Usage of the Specification

Metadata is collected by a crawler using platform APIs;

- find a list of supported platforms [here]().
- Hence, in most cases no additional manual input of metadata is required from developers, since the platforms (such as Wikifactory or OSHWA) already expose the desired metadata via their API
- in case of GitLab or GitHub, the API is not OSH-specific; developers shall provide the metadata in form of a [manifest file](#manifest-file); those manifest files are searchable for the crawler via the GitHub/GitLab-API (see [#24](https://github.com/OPEN-NEXT/LOSH/issues/24) for details)

### Manifest File

A manifest file is a plain text file in a repository containing metadata for a OSH module.

As outlined in the [basic usage of the specification](#basic-usage-of-the-specification),
the provision of a manifest file is specifically necessary when metadata cannot be accessed via the platform API
(as in the case of GitLab or GitHub for example). 

#### Location & Naming Convention

- A repository shall contain exactly one manifest file
- in the root directory of the repository,
- named `okh.toml`,
- using the TOML [TOML file format](https://github.com/toml-lang/toml/releases/tag/1.0.0) and
- follow the requirements of this specification\
  Please see our linked templates for this; they'll make your life easier..

#### File Path Conventions

--


We may allow more file formats in the future.

**NOTE 1 to entry:**\
One of the most important fields is the `version`.
The crawler will _only check for new versions_ when crawling is performed.
We rely on manual changes in the manifest file to keep our knowledge base clean
from 'work on progress'.
So whenever you make a new release
or think those changes in your documentation are worth an update on Wikibase
→ **update the version in the manifest file.**\
Otherwise, no changes will be synched.

# metadata fields

In the following, data fields will be referenced by their TOML key (manifest files are written in TOML).
Their corresponding TURTLE key (the ontology is written in TURTLE) is named explicitly.

## pre-filled or filled by the crawler

- `okhv` [string]
  - = "okh-losh" for all data coming
  - version of the OKH standard used
- `data-source` [string]
  - origin of metadata collected by the crawler (e.g. GitHub, Wikifactory)
  - NOTE: not an actual TOML key since this is set by the crawler directly in RDF

## metadata fields for OSH modules

- `name` [string]
  - working title of the OSH module
- `repo` [URL]
  - reference to repository in which the technical documentation is developed
- `version` [string]
  - version of the module
  - following the [semantic versioning scheme v2.0.0](https://semver.org/#semantic-versioning-200)
- `release` [URL]
  - reference to release package of this version of the OSH module
- `license` [string]
  - [SPDX ID](https://spdx.org/licenses/) of the license used
  - if no SPDX key is available yet, use URL to legal code of the license instead
  - NOTE: When no SPDX key is found by the crawler, metadata won't be uploaded to LOSH until the alternative license has been whitelisted by maintainers. At LOSH we need to make sure that all results are actually open source.
- `licensor` [string]
  - licensor (mostly the originator) of the OSH module 
- `organisation` [string]
  - organisation of the licensor
- `readme` [file-path]
  - relative or absolute path to the readme file
  - e.g. `README.md`
- `image` [file-path]
  - relative or absolute path to one (!) representative image of the OSH module
- `documentation-language` [string]
  - IETF language tag for the language in which the documentation is written
- `technology-readiness-level` [string]
  - OTRL-ID representing the development stage of the OSH module
  - get it from here: <https://github.com/OPEN-NEXT/LOSH/raw/master/OTRL.ttl>
- `documentation-readiness-level` [string]
  - ODRL-ID representing the development stage of the documentation
  - get it from here: <https://github.com/OPEN-NEXT/LOSH/raw/master/OTRL.ttl>
- `attestation` [URL]
  - reference to a valid attestation that the documentation is complete and fully qualifies as open source hardware
  - issuing conformity assessment bodies according to DIN SPEC 3105-2:
    - [Open Hardware Observatory](https://en.oho.wiki/wiki/Request_certification_for_your_project)
    - [Open Source Ecology Germany](https://gitlab.opensourceecology.de/verein/projekte/cab/CAB)
  - [OSHWA certification programme](https://certification.oshwa.org/)
- `function` [string]
  - functional description, e.g. what it actually does, what problem it solves, for whom, under which conditions etc.
    so if you wish that someone finds & uses your okh specifically e.g. for COVID-19-crisis response, include relevant keywords in this field\
    optional: description of input, output and interfaces
- `standard-compliance` [string]
  - document number of the official standard the OSH module complies
  - e.g. `DIN EN 1335`
  - multiple inputs possible (with one entry each)
- `cpc-patent-class` [CPC-ID]
  - patent class identifier of the Cooperative Patent Classification that describes best the field of technology of the OSH module
  - get it from here: <https://worldwide.espacenet.com/classification>
  - e.g. `D03D 35/00`
- `tsdc` [TsDC-ID]
  - identifier of the applying Technology-specific Documentation Criteria (TsDC) according to DIN SPEC 3105-1
  - get it from here: <https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/oh-tsdc.ttl>
  - e.g. `MEC`
  - multiple inputs possible (with one entry each)
- `bom` [file-path]
  - relative or absolute path to the bill of materials
  - e.g. `bom.csv`
- `manufacturing-instructions` [file-path]
  - relative or absolute path to manufacturing instructions
  - e.g. `/Documentation/Assembly_Guide/AssemblyGuide.md`
  - multiple inputs possible (with one entry each)
`user-manual` = "/Documentation/User_Guide/UserGuide.md"
- `user-manual` [file-path]
  - relative or absolute path to user manual

## metadata fields for parts

- `name` [string]
  - working title of the part
- `image` [file-path]
  - relative or absolute path to one (!) representative image of the OSH module
- `tsdc` [TsDC-ID]
  - identifier of the applying Technology-specific Documentation Criteria (TsDC) according to DIN SPEC 3105-1
  - get it from here: <https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/oh-tsdc.ttl>
  - e.g. `3DP`
  - multiple inputs possible (with one entry each)
- `source` [file-path]
  - relative or absolute path to source file (e.g. native CAD file)
  - e.g. `/3D-parts/part1.scad`
  - multiple inputs possible (with one entry each)
- `export` [file-path]
  - relative or absolute path to export file (e.g. STEP export of 3D model or PDF export of drawing)
  - e.g. `/3D-parts/part1.STP`
  - multiple inputs possible (with one entry each)

## software

- `release` [URL]
  - unambiguous refrence to the software release used for this version of the OSH module
  - e.g. `https://github.com/arduino/ArduinoCore-mbed/releases/tag/1.3.2`
- `installation-guide` [URL]
  - unambiguous refrence to the installation guide for the corresponding software release
  - e.g. `https://github.com/arduino/ArduinoCore-mbed/blob/a2c06d768f5ebb6821ae6505b2032ee58f4ef70d/README.md`


## production metadata

## for modules and parts

- `outer-dimension` [openSCAD-primitive]
  - openSCAD primitive describing shape and size of the module or part
  - e.g. `cube(size = [400,350,150]`
- `outer-dimension-dim`
  - dimension of `outer-dimension`
  - e.g. `mm`

## for parts only

- `material` [string]
  - reference of material used for this part
  - e.g. `PLA`

# Further References

Find a template for manifest files in the GitHub repository here:\
<https://github.com/OPEN-NEXT/LOSH/blob/master/sample_data/okh-TEMPLATE.toml>
