---
title: How to fill out the `okh-TEMPLATE.toml`
date: 17.11.2021
version: v0.1
author: Martin Häuer
...

This guide is here to help you when creating a manifest file using the `okh-TEMPLATE.toml`.
A manifest file is a plain text [TOML](https://toml.io/en/) file that makes relevant metadata about your open source hardware project publicly available in a more machine-readable manner (e.g. the "Krawler" which collects those files to import corresponding projects to [LOSH](losh.opennext.eu)).
It follows the [OKH-LOSHv1 specification]().
So, all you need to do is filling out the template and publish it on GitHub (e.g. in your project repository or via <https://github.com/OPEN-NEXT/LOSH-list/>).

# Data fields

All fields are linked to their more detailled specification.
Mandatory fields are bold.
If some data fields are not applicable in your case, please remove them from the manifest file.

- [okhv](https://github.com/OPEN-NEXT/OKH-LOSH/blob/master/OKH-LOSH.md#for-osh-modules-only)
  - automatically filled; NOT to be changed by you
- **[name](https://github.com/OPEN-NEXT/OKH-LOSH/blob/master/OKH-LOSH.md#metadata-fields-for-osh-modules)**
  - name or working title of your hardware project
- **[repo](https://github.com/OPEN-NEXT/OKH-LOSH/blob/master/OKH-LOSH.md#metadata-fields-for-osh-modules)**
  - link to the repository of your hardware project (= wthere the documentation is developed)
- **[version](https://github.com/OPEN-NEXT/OKH-LOSH/blob/master/OKH-LOSH.md#metadata-fields-for-osh-modules)**
  - version of your hardware project; when you change this field, the crawler will recognise this as a new version and upload it to LOSH; **otherwise not**
- [release](https://github.com/OPEN-NEXT/OKH-LOSH/blob/master/OKH-LOSH.md#metadata-fields-for-osh-modules)
  - URL to the release package of this version of your hardware project
- **[license](https://github.com/OPEN-NEXT/OKH-LOSH/blob/master/OKH-LOSH.md#metadata-fields-for-osh-modules)**
  - SPDX-ID of the license you chose; get from here: <https://spdx.org/licenses/>; e.g. CERN-OHL-S-2.0
- **[licensor](https://github.com/OPEN-NEXT/OKH-LOSH/blob/master/OKH-LOSH.md#metadata-fields-for-osh-modules)**
  - the official licensor of your hardware project; in most cases this will be the originator (may be you)
- [organisation]
  - the organisation behind the development of this hardware project
- [readme](https://github.com/OPEN-NEXT/OKH-LOSH/blob/master/OKH-LOSH.md#metadata-fields-for-osh-modules)
  - file path to the README file
contribution-guide = "CONTRIBUTING.md" # relative path from the root directory IF the manifest file is _in_ the project's repositoy; use an URL otherwise
image = "xxx.jpg" # relative path from the root directory IF the manifest file is _in_ the project's repositoy; use an URL otherwise
documentation-language = "en-GB"
technology-readiness-level = "OTRL-3" # choose OTRL level from here: <https://github.com/OPEN-NEXT/OKH-LOSH/blob/master/OTRL.md#otrl>
documentation-readiness-level = "ODRL-3" # choose OTRL level from here: <https://github.com/OPEN-NEXT/OKH-LOSH/blob/master/OTRL.md#odrl>
attestation = "https://certification.oshwa.org/cl000001.html" # URL to a public proof that the module has been certified as open source hardware
publication = "https://doi.org/10.1371/journal.pone.0193087" # Permalink (e.g.) DOI to a _scientific_ (that is: peer reviewed) publication that _contains_ the design files
**function** = "xxx" # = a short description of what the hardware is & does / what problem it solves
standard-compliance = "DIN EN 1335" # if applicable
cpc-patent-class = "D03D 35/00" # get CPC-ID from here <https://worldwide.espacenet.com/classification>
tsdc = "MEC" # defines the manufacturing processes involved for this project; multiple entries possible; get from here: https://gitlab.com/OSEGermany/oh-tsdc/-/blob/master/oh-tsdc.ttl#L97
bom = "BoM.csv" # relative path from the root directory IF the manifest file is _in_ the project's repositoy; use an URL otherwise
manufacturing-instructions = "/Documentation/Assembly_Guide/AssemblyGuide.md" # relative path from the root directory IF the manifest file is _in_ the project's repositoy; use an URL otherwise
user-manual = "/Documentation/User_Guide/UserGuide.md" # relative path from the root directory IF the manifest file is _in_ the project's repositoy; use an URL otherwise
outer-dimension-dim = "mm" # dimension of `outer-dimension` below (e.g. millimeter)
outer-dimension = "cube(size = [400,350,150])" # OpenSCAD primitive describing the outer shape; cylinders and spheres also possible

[[part]] # section to link essential files for each self-designed component of this project
name = "your-awesome-part"
image = "xxx.jpg" # relative path from the root directory IF the manifest file is _in_ the project's repositoy; use an URL otherwise
tsdc = "3DP"
source = "xxx.scad" # multiple entries possible; relative path from the root directory IF the manifest file is _in_ the project's repositoy; use an URL otherwise
export = [ # multiple entries possible; relative path from the root directory IF the manifest file is _in_ the project's repositoy; use an URL otherwise
  "xxx.pdf",
  "xxx.stl"
]
material = "PLA" # multiple entries possible
outer-dimension-dim = "mm" # dimension of `outer-dimension` below (e.g. millimeter)
outer-dimension = "cube(size = [120,100,3])" # OpenSCAD primitive describing the outer shape; cylinders and spheres also possible

[[software]]
release = "https://github.com/arduino/ArduinoCore-mbed/releases/tag/1.3.2"
installation-guide = "https://github.com/arduino/ArduinoCore-mbed/blob/a2c06d768f5ebb6821ae6505b2032ee58f4ef70d/README.md"

# General

- [manifest file name & location](https://github.com/OPEN-NEXT/OKH-LOSH/blob/master/OKH-LOSH.md#location--naming-convention)
  - name it `okh-PROJECTNAME.toml` (replacing `PROJECTNAME` with the name of your project) or simply `okh.toml`; it is important that `okh` remains part of of the file name and that you use the `TOML` format
  - place it directly into the root directory of the project, NOT in a subfolder or so
- [file paths](https://github.com/OPEN-NEXT/OKH-LOSH/blob/master/OKH-LOSH.md#file-path-conventions)
  - use a relative path from the root directory IF the manifest file is _in_ the project's repositoy; use an URL otherwise
- multiple entries in TOML files
  - this applies for all TOML files, just do:

  ```TOML
  some-data-field = [
  "entry1",
  "entry2"
  ]
  ```
