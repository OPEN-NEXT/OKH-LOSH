# Hot / shortlist (v1.0)

## use cases / features (unsorted)

in short:
- for developers: facilitate re-use of design
- for users (& developers): 
  - increase discoverability of OSH
  - replace manual packaging; metadata shall enable a download button for:
      - resource to check: https://github.com/kanzure/skdb (**apt-get for hardware**)
    - production files (export only)
    - developer files (sources only)
    - complete clone (export + sources)
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

### considered user stories from OPEN!NEXT (T3.1)

**direct** = covered by the current scope
**indirect** = supported by the current scope &/ on the agenda for future scopes

| **Number** | **Group name** | **Perspective** | **User story** | **Aim** | **Purpose** | **Additional considerations** | T3.3. impact | comment |
|---|---|---|---|---|---|---|---|---|---|
| U1/5 | Community management | Project owner | Curation of community content | Effective community collaboration | To ensure the users are not overwhelmed with irrelevant data |     | direct |     |
| U3/1 | Documentation | Product owner &/ Community | Definition of functionalities | Knowledge distribution | So that skilled and non-skilled community can understand and work with it. This supports reuse of knowledge |     | direct |     |
| U3/4 | Documentation | Community | Documentation of Safety standards used/followed | Complete documentation | Improve safety |     | direct |     |
| U3/8 | Documentation | Community | Read & understand documentation | Find right relevant information | Efficient reading and understanding of relevant documentation | \- Separating documentation by developers into process documentation (step by step) and instructions (how to do it)  <br>-Consider non technical users | direct |     |
| U5/2 | Interoperability | Community | Traceability of variations of a product | Connecting variations of a product on different platforms | Overview of variations (Customization) | \- Families of projects  <br>\- Traceability of similar projects | direct |     |
| U5/3 | Interoperability | Community / Project owner | Connecting various project entities | Traceability across entities in a project | Understand the structure and connections among various entities (knowledge connection) | \- Library of parts to BOM | direct |     |
| U7/1 | Status | Community | Identify status of project | Aid search ability & be aware of the contents of the project | Enable conscious reusability and reduce risk of failure | \- Remade status updates  <br>\- Impact indication  <br>\- Availability/level of documentation  <br>-Enable to follow a project, get notifications  <br>\- Rate the quality of a project | direct |     |
| U8/1 | Quality | Company | Differentiate level of professionalism | Able to judge/differentiate online project with respect to the professional competitive products on the market | Helping in differentiate the level of maturity in the projects and look deeper into the right information |     | direct |     |
| U12/2 | Guidelines | Project owner | Share instructions for manufacturing | To manufacture the right product the right way | Ensure that quality, time and process expectations are held up | -Educate manufacturers  <br>-Develop standard for sharing manufacturing information from project owner to community/manufacturer | direct | …if there are instructions \_and\_ if they are linked |
| U12/7 | Guidelines | Community / company | Guide for service and maintenance | Know how to service and maintain | Enable uncomplicated and inexpensive service and maintenance |     | direct | via linked documentation |
| U14/3 | Development platform | Project owner | Supported OSH file formats | Accessibility of files in OSH community | Improve outreach of files |     | direct | regulated via DIN SPEC 3105 |
| U18/1 | Discoverability | Community / Project owner | Finding relevant information/ projects | Categorized insights | Quick and efficient discoverability of information | \- Project templates to showcase and promote projects  <br>\- Discoverability based on technologies used  <br>\- Comparing existing projects | direct |     |
| U20/1 | Standards | Community | Metric system compatibility | work and support with various metric systems | Ensure metric parameters are interpreted in the same sense across various countries | \- Materials | direct | will be adressed in the TsDC |
| U20/2 | Standards | Project owner | Find and use standardized components | Reuse standard components | Improve speed, cost reduction and work with commonly available components |     | direct |     |
| U1/2 | Community management | Project owner | Finding and attracting the right collaborators | Growth and effective contribution | Growth & sustenance of community collaboration | \- Including companies  <br>\- Build heterogeneous teams (to encourage development of all aspects of a project)  <br>\- Skill based categorization | indirect |     |
| U3/3 | Documentation | Community | Documentation of IT tools used | Complete documentation | Enable reusability | -The level of skill needed to use the tools | indirect |     |
| U3/7 | Documentation | Project owner/ Community | Up to date documents | Complete & up to date documentation | Avoid outdated information |     | indirect | metadata refers to documents for a specific release |
| U4/2 | Informal knowledge documentation | Community | Assign knowledge communicated in informal channels to suitable topic/topics | Structured and well connected knowledge | Knowledge discovery | In forum, chats, etc. | indirect | knowledge can be just linked already; future DBs may support that so Wikibase helps connecting the dots |
| U6/2 | Collaborative Production | Community/Project owner | Viable prototyping of small quantities | reduce cost of prototyping | small quantities are expensive to produce than large mass production |     | indirect | manufacturing steps & assembly can be easier split across different manufacturers; a future DB of manufacturers should additionally support that |
| U6/3 | Collaborative Production | Project owner / Company | Identify right partner for manufacturing/supplying | Find and collaborate with the right partner | Quick matchmaking to encourage manufacturing/production | \- Right partner for Open distributed manufacturing/supplying (Marketplace)  <br>\- Profile, experience, certifications of manufacturer/supplier  <br>\- To generate an ecosystem  <br>\- As a service from Fablab network  <br>\- Find suitable workshop/Makerspace  <br>\- A map with competencies to identify gaps and possibilities | indirect | requires a DB for manufactures, but OSH metadata should deliver sufficient information from this side for matchmaking |
| U6/4 | Collaborative Production | Company/ Fablab/ Makerspace | Cost sharing for certifications & regulations | To reduce cost and pressure of certifications on those who manufacture it | Shared & cost effective process of certification |     | indirect | CE cert. can be modular and shared via OSH modules as part of their techn. docu. |
| U10/1 | Certification | Company / community | Funding for certification | Improve safety of products in market | Encourage certification |     | indirect | we can filter for certified projects …which are more likely to get reused, reproduced etc. |
| U10/2 | Certification | Project owner | Find the right safety standard | Generate safe projects | Promote safety |     | indirect | a DB of standards could be matched with function category |
| U10/3 | Certification | Company / community | Find certification information | Find and collaborate on certification | Tackle the difficulties in certification processes |     | indirect | a DB of certification requirements could be matched with function category and standards |
| U12/3 | Guidelines | Project owner | Guide the users to customize design | To enable open customization of designs by various users | Generate innovative ideas and enable customization of existing designs |     | indirect | via linked contribution guides |
| U12/6 | Guidelines | Community | Guide for contributing | Know how to contribute | Maintain quality and standards of initial project/company |     | indirect | via linked contribution guides |
| U12/9 | Guidelines | Community / Project owner | Guide for using OSH sharing platform | Promote sharing from everyone | Enable uncomplicated sharing experience for community with various skills |     | indirect | not a guide, but this metadata is porteable to other platforms (inexpensive publishing) + crawled projects are directly published on OHO |
| U13/1 | Collaborative product development | Community | Low complexity of product | Make product reproducible using lesser efforts/process steps | Broaden reproduction/manufacturing | \- Reducing supply chain of parts to be manufactured | indirect | approach supports modularity, modules are more likely to be reused |
| U13/8 | Collaborative product development | Project owner / community / company | Find right OSH tool | Identifying the right tool for a given task | Using OSH tools for OSD |     | indirect | we could build a DB of FOSS tools and match it to the data formats of a certain module &/ its TsDC-ID |
| U14/2 | Development platform | Project owner | Version management | Systematic management of collaborative product development | Organize and control revisions | \- Reason of change  <br>\- What was changed  <br>\- What can still/must be changed  <br>\- Connecting changes | indirect | not directly for development, but an overview is given, yes |
| U14/6 | Development platform | Project owner/ Company | Support rebuilds | Supportive and qualitative collaboration | Encourage and guide community |     | indirect | find compatible modules and reduce your development/maintenance work |
| U16/1 | Community maintained project | Project owner | Develop a community based ecosystem which maintains a project | Community based project development and continuous improvement | Continuous development even if the original designer is not active anymore |     | indirect | modularity is key; the more complex a project is the less likely some new extern will pick it up and read into it |
| U17/2 | Fablab/ Makerspace | Company / community | Testing | Collaborative testing | Aid in sharing resources and knowledge for collaborative testing | \- Electronics  <br>\- Automotive | indirect | as for standards, a DB of standard test procedures can be linked to modules |
| U17/5 | Fablab/ Makerspace | Company / community | Services provided by Fablabs | Transparent services picture of Fablabs | More machines and faster access to resources (Components ecosystem) | \- Declare competencies  <br>\- Declare infrastructure  <br>\- Cost clarification | indirect | manufacturers (including fablabs) can be an additional DB (as OKW is pointing out) |
| U19/1 | Collaborative Testing | Community | Testing of prototype developed from OSH project | To develop a prototype that can be safely used | Ensure safety and quality | \- Involvement of Fablabs  <br>\- Consideration specific sectors (electronic, automobile, medical, etc.) | indirect |     |
| U19/2 | Collaborative Testing | Community | Remote hardware testing and prototyping | Prototype & Test hardware from anywhere | Complex products which cannot be built by everyone has a chance to be worked on and improved by the community | \- Involve Fablabs | indirect |     |

## derived competency questions (unsorted)

- Is or has this OSH Module been used in other OSH Modules? If yes, which?
- Which OSH Modules fulfill are part of this function category x?
- Are there variants/version of or similar OSH Modules like OSH Module X?
  - to be translated into:\
  "How 'identical' are two different OSH Modules?" (← focus on self-designed parts rather than standard components) &\
  "Show me the versions of this OSHM/POSH"
- Which software is required to modify the technical documetation of this OSH Module/POSH?
- Has this OSH Module been certfied in any way? Is it using specific standards?
- What's the development status of a given OSH Module?

## practical examples

### design reuse vs. COVID-19

I am a manufacturer and want to build ventilators for the local hospital. So I'm checking for related OSH projects that 
- have a complete technical documentation 
- are using specific standards
- have a CE certification
- don't create too much subsequent costs (e.g. for software when modifying the design).

In case I'm not happy with any of the results I may choose to design my own open source ventilator, recycling some of the designs, I found, I'll ask myself/the Wikibase instance:
- Which modules/components have been used in various modules?
- Which modules/components are available matching my software requirements? (e.g. specific CAD software) 
- How many parts (self-designed, standard, proprietary, total) are involved in a specific OSH Module?

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
