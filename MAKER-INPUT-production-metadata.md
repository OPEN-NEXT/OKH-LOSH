---
title: Specification for Production Metadata
subtitle: Input from WP4/WP5 Partners
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

- material
- outer dimensions
- mass
- smallest tolerance class [according to ISO 286]

## 3DP

- material
  - material quantity [g]/  filament diameter and length [mm] [mm]
  - material specific requirements
    for ABS: enclosure, warm constant room temperature, air circulation, bed temperature
    heating bed temperature [°]
    extruder temperature [°]
    filament brand
- outer dimensions
- expected print duration
- print parameters
  - infill [%]
  - rafts [bool]
  - supports [bool]
  - resolution [mm] (layer thickness)
  - optional print speed [mm/s]
  - optional outer perimeter speed [mm/s]
  - optional infill speed [mm/s]
  - optional printer speed [mm/s]
  - optional shell thickness [mm]
  - optional top/bottom thickness [mm]
- extruder nozzle diameter [mm]

## WELDING

## PCB

## SOFTWARE

- hardware requirements (specific board; e.g. software only runs on Ardiuno)
- compiler
- pogramming language
- connection (special) cable, flashing hardware

## LASER CUTTER

- material
  - material thickness [mm]
  - required laser power [watt]
- outer dimensions 
- expected duration [s]
  - cutting length [mm]
- cutting speed [mm/s]

# free feedback

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

title: O!N Production Metadata | Joost
...

## CNC

- smallest inner radius
- sharp inner corners [bool]
- number of axes
- number of planes of milling

## 3DP

- shell thickness & top/bottom thickness → requirement
- all other optional print parameters are not so important
- rest is fine
- add: printing method (FDM, SLA,…)

## WELDING

- material (for each part)
- material thickness (for each part)
- welding process
- (welder) certification required
- post-treatments of the weld

## Post-Processing

- surface finishing (polishing, coating etc.) ← important

## LASER CUTTING

- required laser power → not necessary
- expected duration [s] → not necessary
- cutting length [mm] → not necessary
- cutting speed [mm/s] → not necessary

- material thickness [mm]
- engraving? [bool]
- depth of engraving [mm]
- resolution of engraving [mm]

# free feedback

- https://www.hubs.com/ is a great source for metadata (by uploading sample files)
