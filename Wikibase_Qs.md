# Scope of the ontology

## Hot / shortlist (v1.0)

### use cases / features (unsorted)

in short:

- for developers: facilitate re-use of design
- for users (& developers):
  - increase discoverability of OSH
  - replace manual packaging; metadata shall enable a download button for: <!--- resource to check: <https://github.com/kanzure/skdb> (**apt-get for hardware**) --->
    - production files (export only)
    - developer files (sources only)
    - complete clone (export + sources)
    - export BoM (like [sBoM](#simplified-bom-sbom))
- for the future: be compatible & extendable

to be shortened:

- Linked Open Hardware
  - portable metadata → OSH can be published on various platforms (and is synced via wikibase)
  - map of usage, hence compatibility between OSH Modules (this module is also included here and there)
  - don't reinvent the wheel, see what others have used in a similar case
  - reduce (electronic) waste; circular economy
    - represent OSH & proprietary HW by reasonable metadata; see connections, assess compatibility
- link to other DBs
  - wikidata
  - Journal of Open Hardware
  - …
- Find OSH in a specific field
  - e.g. search for corona-related projects
    - add optional field in metadata: related topics/tags
    - (? maybe not reasonable →) design specific searches (e.g. corona also includes the tags ventilators, face shields etc.)
- OSHWA-compliant license?
- get TsDC
- filter for 'real' OSH
- filter for standards/certification
- filter for file formats
  - which (costly) licenses are required?
  - what does it cost me to enter?
    (so comparing the required with the existent licenses on my side)

#### considered user stories from OPEN!NEXT (T3.1)

**direct** = covered by the current scope
**indirect** = supported by the current scope &/ on the agenda for future scopes

…table outsourced for better readability; find it [here](user-stories-t3-1.csv)

### derived competency questions (unsorted)

- Is or has this OSH Module been used in other OSH Modules? If yes, which?
- Which OSH Modules fulfill are part of this function category x?
- Are there variants/version of or similar OSH Modules like OSH Module X?
  - to be translated into:\
  "How 'identical' are two different OSH Modules?" (← focus on self-designed parts rather than standard components) &\
  "Show me the versions of this OSHM/POSH"
- Which software is required to modify the technical documetation of this OSH Module/POSH?
- Has this OSH Module been certfied in any way? Is it using specific standards?
- What's the development status & version of a given OSH Module or its documentation release?
- What are the requirements for the technical documentation for a specific piece of OSH?
  - REMARK 1: this may require translating generic DIN SPEC requirements + TsDC into Wikidata-compatible formats
  - REMARK 2: this may enable automated pre-checking of compliance of documentation releases against the requirements of DIN SPEC 3105-1 (and the corresponding TsDC)
- Where are the files (source & export) I need to build/modify this OSH?
- What are production requiremnts to build a certain piece of OSH? (e.g. tolerances, material,…)
- What's the license?
- Where can I contribute or find more specific information?
- In which language is this documentation release available?

### practical examples

#### design reuse vs. COVID-19

I am a manufacturer and want to build ventilators for the local hospital. So I'm checking for related OSH projects that

- have a complete technical documentation
- are using specific standards
- have a CE certification
- don't create too much subsequent costs (e.g. for software when modifying the design).

In case I'm not happy with any of the results I may choose to design my own open source ventilator, recycling some of the designs, I found, I'll ask myself/the Wikibase instance:

- Which modules/components have been used in various modules?
- Which modules/components are available matching my software requirements? (e.g. specific CAD software)
- How many parts (self-designed, standard, proprietary, total) are involved in a specific OSH Module?

## Question Pool / longlist

### future scopes

- library of standards & standard parts
  - unambiguous referencing (even for outdated standards)
  - find standards in your field of technology; specific use case for newcomers in a certain field (e.g. research institutes), discussed in a meeting between HSU Hamburg & DIN (COVID-19 crisis response)
- library of manufacturers
  - enable a 'buy button' for OSH Modules
  - Open Know-Where (part of the Open Know-How network) is working on a metadata standard for manufacturers, tools and stock items (materials etc.)

### project/team/contributors

- How many contributors involved?
- Which organisations involved?
- Where are contributors located?
- What other projects contributors contribute to?
- education/employment details of contributors
- How many forks? → + same information about forks as about project itself
- Who created issues?
- Who responded to issues?
- Who solved issues?
- How fast is support?
- accepted ways of support
  - contribution guide existent?\
    (+ further, yet hardly trackable questions regarding openness of the development)
  - Patreon/PayPal/GoFundMe?
- Who's using this product?

- credits for developers, reviewers etc.
- matching reviewers & contributors via TsDC-ID

### product/documentation

- this thing can be bought here
- manufacturer matchmaking
  - appropriate tools/manufacturers to build this
    (including tolerances, surface properties)
  - → search for manufacturers as for flights
      (price, location, development time, delivery etc.)
  - → combine manufacturers as lego suppliers (see Lars)\
  …+ optional "trusted supply chain" (verified manufacturers and/or favourites)
  - → automated templates for procurement (to notify manufatcurers)
- certified/'real' OSH? (DIN SPEC 3105 / OSHWA cert)
- any product certification or CE mark something?
- manifest file/listed on [OHO.wiki](https://OHO.wiki)?
- standards used in the design (≠ standard parts used)
  (crucial for big customers; see e.g. office furniture)
- which file formats have been used?
  - which (costly) licenses are required?
  - what does it cost me to enter?
    (so comparing the required with the existent licenses on my side)
- **define reasonable metadata for self-designed components**
  - same metadata as standardised semi-finished components & standard parts (material properties, measurements, tolerances, surface, weight etc.)
  - → full product data is stored as LOD → graph-based assessment of production, static resistance, compatibility with other hardware, change management… bloody fucking everything!

#### standard parts library

- references
  - including identical obsolete standards (as for screws)
- properties
- where to get them

#### OSH module library

- references
- properties
- input/signal/output (black-box interface; EMS model)
- compatible with… (=proofed/designed for) ← linking grows by using this library

#### science extras

- this hardware has been mentioned in this publications in that journals
- this hardware builds upon publications here and there
- find appropriate peer-reviewers (e.g. via certification)

#### engineering extras

- library of boundary condition (e.g. forces due to snow loads, load cycles for cranes)
- emission tables (e.g. max. values for electronics in this country)
- conditions DB for product certification
  - e.g. use of these standards for medical devices in the EU
  - past these tests for your CE mark
    - [technology category](https://en.wikipedia.org/wiki/CE_marking#Product_groups)
    - where can I perform these tests?
- manufacturing settings
  - working welding parameters
  - GCode for this specific 3D-Printer model / CNC milling machine
  - …

#### circular economy

- see [OHS 3105-1 issue #7]([https://gitlab.com/OSEGermany/OHS/-/issues/7)
- network of modules in use
  - tracking of reproduction as a side effect
  - marketplace for maintenance parts
- mapping of open/standardised interfaces

#### guideline extras

- match guideline resources to project
  (liability? →\
  OSH Guideline for legal issues;\
  Open Source Business Models;\
  technology-specific documentation guidelines;\
  licensing guidelines)

### Problems to solve

- reusage of designs
- indirect: reusage of sub-assemblies via modular machine design
- avoid having adjusted CAD files, specifications etc. spread over a dozen mails
  when (as a developer) talking with manufacturers
- quality control
  - a) for documentation
    - find certified/peer-reviewed documentation
    - see how many people build this thing
      (by commissioning these external manufacturers)

### simplified BoM (sBoM)

**Intro:**

- meant to be easy to read, crawl and use
- references to all parts and files necessary to build the [OSH-Module](#osh-module) following [TsDC](https://gitlab.com/OSEGermany/oh-tsdc/)-requirements
  - column `Reference` includes single entries only which are either
    - URLs to a [POSH](#piece-of-osh-posh)
    - unambiguous references to standard or purchased parts (which can be either URLs or designations)
    - URLs to other [OSH-Modules](#osh-module)
- subassemblies are _not_ represented as individual modules, but included via structured pos. numbers

EXAMPLE:

[**This section is OUTDATED; simplified BoMs now may include subassemblies via appropriate pos. numbers which makes linking to ASM-specific metadata files obsolete**]

| Pos. | Name         | Units | Type            | Reference                                                                           |
|------|--------------|-------|-----------------|-------------------------------------------------------------------------------------|
| 1    | casing       | 2     | OSH Component   | link to [POSH file](#piece-of-osh-posh), similar to [this](#mechanical-component-posh-mec) one                                      |
| 2    | screw        | 4     | standard part   | standard designation                                                                |
| 3    | gear box     | 1     | OSH Module      | link to [OSH-Module](#osh-module)                                                   |
| 4    | Raspberry Pi | 1     | purchased part  | unambiguous reference (not standardised)                                            |
| 5    | holder       | 1     | OSH Subassembly | link to [POSH file](#piece-of-osh-posh), similar to [this](#mechanical-component-posh-mec) one                                      |
| 5.1  | bracket      | 2     | OSH Component   | link to [POSH file](#piece-of-osh-posh), similar to [this](#mechanical-component-posh-mec) one                                      |
| 5.2  | screw        | 2     | standard part   | standard designation                                                                |
| 5.3  | arm          | 2     | OSH Component   | link to [POSH file](#piece-of-osh-posh), similar to [this](#mechanical-component-posh-mec) one                                      |
| 6    | controller   | 1     | OSH Module      | link to link to [OSH-Module](#osh-module), similar to [this](#pcb-posh-asm-pcb) one |
