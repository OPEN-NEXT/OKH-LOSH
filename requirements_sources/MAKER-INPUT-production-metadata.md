---
title: Specification for Production Metadata
subtitle: Input from WP4/WP5 Partners
history: https://github.com/OPEN-NEXT/OKH-LOSH/commits/36679600facd5b572f012e74cb359ac84eb2d113/MAKER-INPUT-production-metadata.md
...

# Intro & Scope

With this document we aim to pin down the metadata that **makers** need to assess whether or not they can (or want) to produce a certain piece of Open Source Hardware with the tools available (e.g. in their makerspace).\
More specifically _you_ will write this document.
But don't worry, you're not alone.
We contacted numerous people that are willing to share their expertise here. 

**What we need from you now:** Imagine you have been searching for an open source solution on LOSH to solve a specific problem, and found it! (yeah)\
Now, only focussing on the aspect of manufacturing it:

- Let us know **your production category of interest** (e.g. 3D-printed) by opening a new section [below](#content)
- …and the **corresponding data fields (metadata)** that you'd need to assess whether or not it makes sense for you to produce the corresponding part/module yourself or order it somewhere else (e.g. material, size)

Following DIN SPEC 3105-1 we believe that parts of the metadata should apply technology-specific.

**NOTE:** Metadata are not meant to replace the documentation. It should rather provide you with enough data so that you know whether or not it makes sense to take a deeper look into the documentation.

--

**Please consider:** This is a dynamic document.\
The contributor after you will make changes.
So to ensure a consistent chain of contributions, please make sure that your input can be understood by someone who also has a maker-background, but has never spoken to you and hence doesn't know what's in your mind besides the details noted down.
Please be as specific as possible; if you're unsure about certain input/feedback you want to give, just mark it accordingly, so others will know.

If you find data fields or maybe even production categories that don't make sense in the maker context from your perspective, please make a corresponding note there – I'll process this accordingly.

After all willing makers gave their input, I'll tidy up this document and send it back to you (and everyone else), so you can take notice of it's final version.
If there's anything we forgot, got wrong or any other thoughts you want to share when reading the final version → don't hesitate and let us know in a reply on the mail containing this final version.
Everything will be documented, nothing will be forgotten.
Every peace of feedback is valuable and will be read :)

# Content

## CNC

- material [string]
- outer dimensions
- mass
- smallest tolerance class [according to ISO 286]
- smallest inner radius [mm]
- sharp inner corners [bool]
- number of axes [int]
  - comment: machine-specific → out of scope
- number of planes of milling [int]
  - comment: setup for production environment → out of scope

## 3DP

- printing method (FDM, SLA, SLS, MJF, DMLS)
- material [string]
- material quantity [g]/  filament diameter and length [mm]
- material specific requirements
  for ABS: enclosure, warm constant room temperature, air circulation, bed temperature
  heating bed temperature [°]
  extruder temperature [°]
  filament brand 
  - remove request +1
- outer dimensions
- expected print duration
  - remove request +1
- print parameters
  - infill [%]
  - rafts [bool]
  - supports [bool]
  - resolution [mm] (layer thickness)
  - optional print speed [mm/s]
    - remove request +1
  - optional outer perimeter speed [mm/s]
    - remove request +1
  - optional infill speed [mm/s]
    - remove request +1 
  - optional printer speed [mm/s]
    - remove request +1 
  - optional shell thickness [mm]
  - optional top/bottom thickness [mm]
- extruder nozzle diameter [mm]
  - remove request +1

## WELDING

- material (for each part)
  - comment: already defined per part, no extra field needed
- material thickness (for each part)
  - comment: already defined per part, no extra field needed
- welding process
- (welder) certification(s) required
- post-treatments of the weld

## PCB

- size (2D) [mm , mm]
- board-thickness [mm]
- copper-thickness [mm]
- typical-trace-width [mm]
- smallest-trace-width [mm]
- typical-space-copper-copper [mm]
- smallest-space-copper-copper [mm]
- smallest-via-diameter [mm]
- component-sides [1 or 2]
- silkscreen-printing-sides [0, 1 or 2]
- solder-mask-sides [0, 1 or 2]

For multilayer-pcb:
- layer-count [int]
- copper-thickness [array of mm]
- isolator-thickness [array of mm]

## LASER CUTTER

- engraving? [bool]
  - comment: redundant when depth of engraving is given
- depth of engraving [mm]
- resolution of engraving [mm]
  - comment: resolution seems to be given in DPI usually
- material [string]
- material thickness [mm]
- required laser power [watt]
  - remove request +1
- outer dimensions 
- expected duration [s]
  - remove request +1
- cutting length [mm]
  - remove request +1
- cutting speed [mm/s]
  - remove request +1

## Post-Processing

- surface finishing (polishing, coating etc.)
  - comment: important for welding seam finishing

# free feedback

- https://www.hubs.com/ is a great source for productionn metadata (accessible by uploading sample files)

## SOFTWARE

- hardware requirements (specific board; e.g. software only runs on Arduino)
- compiler
- pogramming language
- connection (special) cable, flashing hardware

## Assembly

- tools
- space
- duration

## environmental conditions

- humidity
- temperature
- air circulation
- dust
- fire resistance
- explosion protection
- corrosion resistance

## general metadata

- safety and legal criticality?
- classifaction badges or levels for overall difficulty to build: e.g. DIY (doable with current desktop 3D printers), professional
- target group (e.g. Arduino project may be made for researchers and students): children, industrial students, professionals
- variants/alternatives to the solutions specifically described in the documentation
