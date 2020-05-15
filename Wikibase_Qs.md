# Hot / shortlist (v1.0)

## use cases / features

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
- get TsDC
- filter for 'real' OSH
- filter for standards/certification
- filter for file formats
  - which (costly) licenses are required?
  - what does it cost me to enter?
    (so comparing the required with the existent licenses on my side)

# Question Pool / longlist

These are questions one should be able to pose to the database.

## project/team/contributors

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
- - Who's using this product?

- credits for developers, reviewers etc.
- matching reviewers & contributors via TsDC-ID

## product/documentation

- this thing can be bought here
- manufacturer matchmaking
    - appropriate tools/manufacturers to build this
      (including tolerances, surface properties)
    - → search for manufacturers as for flights
        (price, location, development time, delivery etc.)
    - → combine manufacturers as lego suppliers (see Lars)
        - \+ optional "trusted supply chain" (verified manufacturers and/or favourites)
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

### standard parts library

- references
  - including identical obsolete standards (as for screws)
- properties
- where to get them

### OSH module library

- references
- properties
- input/signal/output (black-box interface; EMS model)
- compatible with… (=proofed/designed for) ← linking grows by using this library

### science extras

- this hardware has been mentioned in this publications in that journals
- this hardware builds upon publications here and there
- find appropriate peer-reviewers (e.g. via certification)

### engineering extras

- library of boundary condition (e.g. forces due to snow loads, 	load cycles for cranes)
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

### circular economy

- see [OHS 3105-1 issue #7]([https://gitlab.com/OSEGermany/OHS/-/issues/7)
- network of modules in use	
    - tracking of reproduction as a side effect
    - marketplace for maintenance parts
- mapping of open/standardised interfaces

### guideline extras

- match guideline resources to project
  (liability? →\
  OSH Guideline for legal issues;\
  Open Source Business Models;\
  technology-specific documentation guidelines;\
  licensing guidelines)

## Problems to solve

- reusage of designs
- indirect: reusage of sub-assemblies via modular machine design
- avoid having adjusted CAD files, specifications etc. spread over a dozen mails
  when (as a developer) talking with manufacturers
- quality control
    - a) for documentation
        - find certified/peer-reviewed documentation
        - see how many people build this thing
          (by commissioning these external manufacturers)
