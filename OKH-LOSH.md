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

# Intro

The work here is based on the [Open Know-How Specification v1.0.0](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#75fb9df0-a7b3-427f-993a-b23fe1c81a58), specifically to make the OKHv1 specification applicable to linked open data and rework data fields after latest research results.\
However, lots of changes have been made so it's hard to still call this a fork.\
After validation this will be proposed to maintainers of the Open Know-How Specification as a new major version of the specification.

**NOTE:** When we talk about "OSH module" we mean the content of a repository.
Open source hardware (OSH) aims to be modular.
Hence it makes a lot of sense to publish each module in an individual repository
(instead of the whole machine in one large repository).
A module is an assembly of various parts that fulfils a certain purpose.
However, there are exceptions, as a standalone 3D-printed part in a git repository could also fulfil a purpose and qualify as a module.

## Scope

OKH-LOSH features the specification for representative metadata of open source hardware (OSH) modules.
An OSH module can be any tangible object for which relevant technical documentation has been published under a license complying with terms stated by the [OSHWA definition](https://oshwa.org/definition); in most cases that will be an assembly of parts fulfilling a defined functions, whereby documentation is published on an online platform of choice (e.g. [GitLab.org](https://gitlab.org/)).
Scope, content and limits of such OSH modules are defined by their developers.
For OKH-LOSHv1 we identify an OSH module by its repository – each module is developed (and version controlled) in one specific repository.

This draft shall support the following user groups:

1. developers (specifically to facilitate **design reuse** and to improve discoverability of hardware)
2. makers & manufacturers (find production-ready OSH)
3. researchers (get a quick overview of the current state of OSH developments)

This draft follows a Linked Open Data approach:

- it's a distributed database; projects and platforms hold their own data; LOSH only collects, connects and displays the data
- data processing is based on RDF (data from manifest files (TOML) and platform APIs (JSON) is translated into RDF by the crawler)
- everything is published under free/open licenses; find the RDF [here](), the crawler [here](), LOSH website [here] and the specification (that you are reading) [here]().

This draft aims to facilitate compliance with DIN SPEC 3105-1.

## Downward Compatibility

We will continue to support [OKHv1.0.0](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1)
YAML files.\
However, we strongly recommend the usage of `OKH-LOSH` if you want to have your project included on LOSH.

Data mapping specification: see [/Data Mapping/data-mapping-OSHWA.md](Data%20Mapping/data-mapping-OKHv1.md)

# General Requirements

## Basic Usage of the Specification

All data, the metadata itself and the technical documentation represented by the metadata, shall be:

- released under a free/open license;
- unambiguously referenceable.

**NOTE to entry:** See requirements for license and release in DIN SPEC 3105-1 [section 3.2](https://gitlab.com/OSEGermany/OHS-3105/-/blob/ohs/DIN_SPEC_3105-1.md#32-free-license-open-license) and [section 3.9](https://gitlab.com/OSEGermany/OHS-3105/-/blob/ohs/DIN_SPEC_3105-1.md#39-documentation-release).

Yet, provision of metadata is fully based on manual input by contributors of the OSH project. Metadata will be collected by a [crawler](https://github.com/OPEN-NEXT/LOSH-Krawler) using the API of supported platforms (find a [full list of supported platforms below](#supported-platforms)).\
Hence, when data is published on a supported platform in compliance with this specification, it becomes automatically available on [LOSH](losh.ose-germany.de) and as Linked Open Data in RDF format [here]().

## Supported Platforms

### GitLab

<!--YET TO BE IMPLEMENTED-->

Data submission requires the use of a [Manifest File](#manifest-file).

The Manifest File is directly available for the crawler via the GitLab-API.\
(See [#24](https://github.com/OPEN-NEXT/LOSH/issues/24) for details.)

URL to platform: <https://gitlab.com/>

### GitHub

Data submission requires the use of a [Manifest File](#manifest-file).

The Manifest File is directly available for the crawler via the GitHub-API.\
(See [#24](https://github.com/OPEN-NEXT/LOSH/issues/24) for details.)

URL to platform: <https://github.com/>

### Appropedia

Data shall be provided using the "Infobox device" template ([version from 15:13, 2 June 2021 by Felipe Schenone](https://www.appropedia.org/Template:Infobox_device)).

The [LOSH Appropedia scraper](https://github.com/OPEN-NEXT/LOSH-Appropedia-Scraper) will upload metadata in form of [Manifest Files](#manifest-file) to the [LOSH-List repository](https://github.com/OPEN-NEXT/LOSH-list) on [GitHub](#github), where it becomes available for the crawler.

URL to platform: <http://appropedia.org/>

Data mapping specification: see [/Data Mapping/data-mapping-Appropedia.md](Data%20Mapping/data-mapping-Appropedia.md)

### Wikifactory

Metadata is embedded by the platform and directly available for the crawler.

URL to the platform: <https://wikifactory.com/>

Data mapping specification: see crawler code [here](https://github.com/OPEN-NEXT/LOSH-krawler/blob/main/krawl/krawl/wfconvert.py)

### OSHWA Certified Projects List

<!--YET TO BE IMPLEMENTED-->

URL to platform: <https://certification.oshwa.org/list.html>

Data mapping specification: see [/Data Mapping/data-mapping-OSHWA.md](Data%20Mapping/data-mapping-OSHWA.md)

## Manifest File

A manifest file is a plain text file in a repository containing metadata for a OSH module.

As outlined in the [basic usage of the specification](#basic-usage-of-the-specification),
the provision of a manifest file is specifically necessary when metadata cannot be accessed via the platform API
(as in the case of GitLab or GitHub for example). 

**NOTE 1 to entry:**\
One of the most important fields is the `version`.
The crawler will _only check for new versions_ when crawling is performed.
We rely on manual changes in the manifest file to keep our knowledge base clean
from 'work on progress'.
So whenever you make a new release
or think those changes in your documentation are worth an update on Wikibase
→ **update the version in the manifest file.**\
Otherwise, no changes will be synched.

### Location & Naming Convention

- A repository shall contain exactly one manifest file
- in the root directory of the repository,
- named `okh.toml`,
- using the [TOML file format](https://github.com/toml-lang/toml/releases/tag/1.0.0)\
  (we may allow more file formats in the future) and
- and follow the requirements of this specification
  Please see our linked templates for this; they'll make your life easier.

### File Path Conventions

For file referencing this specification allows relative and absolute paths.

#### Relative Path

A relative path starts from some directory
the corresponding manifest file is located in.
The file reference _never_ starts with a "`/`"

**EXAMPLE**

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

#### Absolute Path

An absolute path always starts from the root directory (= repository folder).
The file reference _always_ starts with an "`/`"

**EXAMPLE**

`/3DParts/ClampRing/ClampRing.scad`

# Metadata Fields

In the following, data fields will be referenced by their TOML key (manifest files are written in TOML).
Their corresponding TURTLE key (the ontology is written in TURTLE) is named explicitly.

Mandatory entries are bold.\
To summarise: an OSH module must bear reference of:

- the complete legal information (name, license, licensor);
- an unambiguous reference to its repository, where source files are available;
- its specific version;
- the language in which the documentation is written;
- its functional description.

## pre-filled or filled by the crawler

### for OSH modules only

- **`okhv`** [string]
  - version of the OKH standard used
  - = "OKH-LOSHv1.0" for all manifest files following this specification
  - = "OKHv1.0" for all manifest files following [OKHv1.0](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1)
- **`data-source`** [string]
  - origin of metadata collected by the crawler (e.g. GitHub, Wikifactory)
  - NOTE: not an actual TOML key since this is set by the crawler directly in RDF

### for files only

- `file-format` [MIME]
  - from `file-path`
- `perma-URL` [URL]
  - commit-specific URL generated from `file-path`
- `last-requested` [timestamp]
  - timestamp of last time the file access was requested under the `perma-URL`
- `last-seen` [timestamp]
  - timestamp of last time the file was successfully accessed under the `perma-URL`
  
## metadata fields for OSH modules

- **`name`** [string]
  - working title of the OSH module
- **`repo`** [URL]
  - reference to repository in which the technical documentation is developed
-** `version`** [string]
  - version of the module
  - following the [semantic versioning scheme v2.0.0](https://semver.org/#semantic-versioning-200)
- `release` [URL]
  - reference to release package of this version of the OSH module
- **`license`** [string]
  - [SPDX ID](https://spdx.org/licenses/) of the license used
  - if no SPDX key is available yet, use URL to legal code of the license instead
  - NOTE: When no SPDX key is found by the crawler, metadata won't be uploaded to LOSH until the alternative license has been whitelisted by maintainers. At LOSH we need to make sure that all results are actually open source.
- **`licensor`** [string]
  - licensor (mostly the originator) of the OSH module 
- `organisation` [string]
  - organisation of the licensor
- `readme` [file-path]
  - relative or absolute path to the readme file
  - e.g. `README.md`
- `contribution-guide` [file-path]
  - relative or absolute path to the contribution guide
  - e.g. `CONTRIBUTING.md`
- `image` [file-path]
  - relative or absolute path to one (!) representative image of the OSH module
- **`documentation-language`** [string]
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
- **`function`** [string]
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
- `source` [file-path]
  - relative or absolute path to source file (e.g. native CAD file)
  - e.g. `/3D-parts/assembly.asm`
  - multiple inputs possible (with one entry each)
- `export` [file-path]
  - relative or absolute path to export file (e.g. STEP export of 3D model or PDF export of drawing)
  - e.g. `/3D-parts/assembly.STP`
  - multiple inputs possible (with one entry each)
- `auxiliary` [file-path]
  - relative or absolute path to files that are neither source files nor their exports, but still useful in the repository (e.g. KiCAD library files)
  - e.g. `/lib/lib1.lib`
  - multiple inputs possible (with one entry each)

## metadata fields for parts

- **`name`** [string]
  - working title of the part
- `image` [file-path]
  - relative or absolute path to one (!) representative image of the OSH module
- `tsdc` [TsDC-ID]
  - identifier of the applying Technology-specific Documentation Criteria (TsDC) according to DIN SPEC 3105-1
  - get it from here: <https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/oh-tsdc.ttl>
  - e.g. `3DP`
  - multiple inputs possible (with one entry each)
- **`source`** [file-path]
  - relative or absolute path to source file (e.g. native CAD file)
  - e.g. `/3D-parts/part1.scad`
  - multiple inputs possible (with one entry each)
- `export` [file-path]
  - relative or absolute path to export file (e.g. STEP export of 3D model or PDF export of drawing)
  - e.g. `/3D-parts/part1.STP`
  - multiple inputs possible (with one entry each)
- `auxiliary` [file-path]
  - relative or absolute path to files that are neither source files nor their exports, but still useful in the repository (e.g. KiCAD library files)
  - e.g. `/lib/lib1.lib`
  - multiple inputs possible (with one entry each)

## software

- **`release`** [URL]
  - unambiguous refrence to the software release used for this version of the OSH module
  - e.g. `https://github.com/arduino/ArduinoCore-mbed/releases/tag/1.3.2`
- `installation-guide` [URL]
  - unambiguous refrence to the installation guide for the corresponding software release
  - e.g. `https://github.com/arduino/ArduinoCore-mbed/blob/a2c06d768f5ebb6821ae6505b2032ee58f4ef70d/README.md`


## production metadata

### for modules

general:

- `joining-process` [string]
  - designation of the manufacturing process used to connect the parts to an assembly
  - e.g. `hard soldering`
  - multiple inputs possible (with one entry each)
- `outer-dimensions` [openSCAD-primitive]
  - openSCAD primitive describing shape and size of the module
  - e.g. `cube(size = [400,350,150]`

#### PCB

`tsdc:PCB`

- `2d-size-mm` [float , float]
  - edge lenghts of the PCB in mm, separated by a comma
  - e.g. `425 , 425`
- `board-thickness-mm` [float]
  - PCB thickness in mm
  - e.g. `1.57`
- `copper-thickness-mm` [float]
  - copper thickness in mm
  - for the case of multilayer PCB see below `multi-copper-thickness-mm`
  - e.g. `0.15`
- `typical-trace-width-mm` [float]
  - typical trace width in mm used in the PCB design
  - not to confuse with `smallest-trace-width-mm`
  - e.g. `0.3`
- `smallest-trace-width-mm` [float]
  - smallest trace width in mm
  - e.g. `0.15`
- `typical-space-copper-copper-mm` [float]
  - typical distance between 2 copper areas (e.g. 2 traces) in mm
  - not to confuse with `smallest-space-copper-copper-mm`
  - e.g. `0.35`
- `smallest-space-copper-copper-mm` [float]
  - smallest distance between 2 copper areas (e.g. 2 traces) in the PCB design
  - e.g. `0.15`
- `smallest-via-diameter-mm` [float]
  - diameter of the smallest via on the PCB in mm
  - e.g. `0.45`
- `component-sides` [integer]
  - number of sides of the PCB with components (1 or 2)
  - e.g. `1`
- `silkscreen-sides` [integer]
  - number of sides of the PCB with silkscreen printing (0, 1 or 2)
  - e.g. `1`
- `solder-mask-sides` [integer]
  - number of sides of the PCB with solder stop mask (0, 1 or 2)
  - e.g. `1`

In case of multilayer PCB:

- layer-count [integer]
  - number of layers of the PCB
  - e.g. `2`
- `multi-copper-thickness-mm` [array of float entries]
  - copper thickness of all layers in mm
  - e.g. `0.15 , 0.15`
- `multi-isolator-thickness-mm` [array of float entries]
  - e.g. `0.23 , 0.23`

#### Welding

`tsdc:WEL`

- `welding-process` [integer]
  - welding process number according to ISO 4063 (e.g. from [here](https://en.wikipedia.org/wiki/List_of_welding_processes))
  - e.g. `111` for "classic" shielded metal arc welding
- `welder-certification` [string]
  - designation of the certification/qualification required for the welder according to ISO 9606
  - e.g. `EN ISO 9606-1 135 P FW FM1 S t10 PB ml` for MAG welding of multi-layer fillet welds on sheet metal (≥ 3 mm) in horizontal position and FM1 filler material

### for parts only

general:

- `material` [string]
  - reference of material used for this part
  - e.g. `PLA`
- `outer-dimensions-mm` (or `outer-dimensions-cm` etc.) [openSCAD-primitive]
  - openSCAD primitive describing shape and size of the module or part
  - e.g. `cube(size = [400,350,150]`
- `tsdc` [TsDC-ID] (multiple)
  - manufacturing process for which this part has been designed (= technology-specific documentation criteria applying for this part)

#### 3D printing

`tsdc:3DP`

- `printing-process` [string]
  - possible values: FDM, SLA, SLS, MJF, DMLS
- `material` [string]
  - reference of material used for this part
  - e.g. `PLA`
- `mass-g` [float]
  - mass of the part in gramms
- `outer-dimensions-mm` [openSCAD-primitive]
  - openSCAD primitive describing shape and size of the module or part
  - all dimensions in mm
  - e.g. `cube(size = [400,350,150]`
- `infill` [float]
  - print parameter: infill (in %)
- `raft-brim` [bool]
  - 0 = design has no raft or brim
  - 1 = design includes raft or brim
- `supports` [bool]
  - 0 = design has no supports
  - 1 = design includes support(s) 
- `resolution-mm` [float]
  - print parameter: resolution/layer height in mm
- `shell-thickness` [float]
  - shell thickness in mm
- `top-bottom-thickness` [float]
  - top/bottom thickness in mm

#### CNC milling

`tsdc:CNC`

- `material` [string]
  - reference of material used for this part
  - e.g. `1.0715` (EN material number for free machining steel 11SMn30)
- `mass-kg` [float]
  - mass of the part in kilogramms
  - e.g. `12.3`
- `smallest-tolerance-class` [string]
  - smallest tolerance class of measures according to ISO 286
  - e.g. `IT9`
- `smallest-inner-radius-mm` [float]
  - smallest inner radius of corners in mm
  - e.g. `0.5`

#### Laser Cutting

<!---FIXME TsDC-ID-->

- `engraving-depth-mm` [float]
  - depth of engraving in mm in case the part has an engraving
  - e.g. `0.25`
- `resolution-dpi` [integer]
  - resolution of engraving in DPI
  - e.g. `500`
- `material` [string]
  - reference of material used for this part
  - e.g. `acrylic glass`
- `thickness-mm` [float]
  - thickness of the sheet material in mm the laser is supposed to cut through
  - e.g. `1.5`

## Post-Processing

<!---FIXME TsDC-ID-->

- `surcace-finishing-process` [string]
  - designation of the manufacturing process for surface finishing to meet required surface properties
  - e.g. `polishing`
- `outer-dimensions-mm` [openSCAD-primitive]
  - openSCAD primitive describing shape and size of the module or part
  - all dimensions in mm
  - e.g. `cube(size = [400,350,150]`

# Further References

Find a template for manifest files in the GitHub repository here:\
<https://github.com/OPEN-NEXT/LOSH/blob/master/sample_data/okh-TEMPLATE.toml>
