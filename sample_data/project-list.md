# Selection of OSH Modules

## Intro

This is an (yet) unsorted list of OSH Modules whose metadata will serve as a testing sample for the OSHI. We'll contact the projects and ask them to help us creating their metadata in compliance with our standard.

We are aiming for ~20 OSH Modules:

- a lot of simple examples in order to save us time and avoid confusion due to complexity overkill
- 2…5 complex modules so we can assess the required performance of the system needed for complex projects
- some of these modules are preferably linked to each other (I doubt that this will be the case for most projects as design reuse is still a significant issue, but maybe we can find some 'product families' where design reuse happens for different variants of the same module)

The following list will be clustered by topics or function categories people may look for. That way we may also get a feeling for requirements for the functional categorization and whether Wikidata is feasible to solve this question. Those categories are not meant to reflect the whole spectrum of OSH or even its most important categories. However, we can keep that in mind, so feel free to add categories :)

## The list

sources:

- <https://github.com/PubInv/covid19-vent-list#evaluation-of-known-projects>
- several direct contacts
- [OHO targets](https://cloud.opensourceecology.de/s/nry4fWE2yCa2D9d)
- <https://glia.org/>

open:

- <https://en.oho.wiki/wiki/The_OHO_Project_Directory>
- <https://gitlab.com/librespacefoundation>
  - An open source hardware satellite
- <https://github.com/orbitalindex/awesome-space#spacecraft-hardware>
  - List of spacecraft hardware (including ground equipment), some of which are open source hardware
- <https://github.com/Opentrons/ot2>  (ot2 already in the list)
  - Opentrons is a highly commercially successful biology lab automation platform
- precious plastics machines
- wikihouse
- <https://www.latelierpaysan.org/Technical-drawings-tutorials>
- <https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4853539/> (medical devices)
- <https://www.open-raman.org/>
- <https://publiclab.org/> e.g. <https://publiclab.org/wiki/desktop-spectrometry-kit-3-0>
- <https://www.labonthecheap.com/>
- <https://github.com/biohackacademy>
- <https://www.openstructures.net/parts>
  - only individual parts
- <https://www.olimex.com/Products/OLinuXino/>
  - electronics only

Wikimedia sample data (copy from list above):

- [MPPT 1210 HUS](https://github.com/LibreSolar/MPPT-1210-HUS)
- [Corne keyboard](https://github.com/foostan/crkbd)
- [COSI Measure Mechanical System](https://github.com/opensourceimaging/cosi-measure/tree/master/Mechanical%20System)

---

### aerospace & underwater

- [Airpup kite balloon](https://github.com/mathewlippincott/airpup-balloon)
- [FOSSASAT-1](https://fossa.systems/fossasat-1/)
- [JPL Open Source Rover](https://github.com/nasa-jpl/open-source-rover)
- [OpenROV](https://github.com/OpenROV)
- [FOSSASAT-2](https://github.com/FOSSASystems/FOSSASAT-2)
- [FOSSASAT-1B](https://github.com/FOSSASystems/FOSSASAT-1B)

### consumer goods

- [AXIOM](https://eu.axiom-camera.com/)
- [Corne keyboard](https://github.com/foostan/crkbd)
- [EOMA68 computing devices](https://www.crowdsupply.com/eoma68/micro-desktop)
  - 100% open source hardare and libre software/firmeware computers
- [Koruza](http://scientific.koruza.net/index.html)
- [MNT Reform](https://source.mntmn.com/MNT/reform)
- [OttoDIY](https://www.ottodiy.com/)
- [Ultimate Hacking Keyboard](https://github.com/UltimateHackingKeyboard/)
- [Volled Board](https://wikifactory.com/@shad0w/volled-board)
- [Maths Tablet](https://github.com/PubInv/math-tablet)

### developer tools

- [EEZ H24005 BENCH POWER SUPPLY](https://www.envox.hr/eez/bench-power-supply/psu-introduction.html)
- [Pocket Science Lab](https://pslab.io/)
  - part of OPEN!NEXT
- [ULX3S](http://radiona.org/ulx3s/)
- [GlussCon](https://github.com/PubInv/GlussCon)
- [Tetrobot](https://pubinv.github.io/tetrobot/)
- [segmented Helixes](https://github.com/PubInv/segmented-helixes)
- [ot2](https://github.com/Opentrons/ot2)

### energy

#### photovoltaic

- [MPPT 1210 HUS](https://github.com/LibreSolar/MPPT-1210-HUS)
- [openWB](https://github.com/snaptec/openWB)

### lab equipment

- [COSI Measure](https://github.com/opensourceimaging/cosi-measure/)
- [OpenFlexure](https://gitlab.com/openflexure)

### medical

#### basic equipment

- [GliaX-Tourniquet](https://github.com/GliaX/tourniquet)

#### diagnosis

- [Life Sensor](https://www.cadus.org/en/life-sensor)
- [GliaX-Otoscope](https://github.com/GliaX/Otoscope)
- [GliaX-Stethoscope](https://github.com/GliaX/Stethoscope)
  - was peer-reviewed [here](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0193087)
- [Moonrat](https://github.com/PubInv/moonrat/blob/master/README.md)
- [Rapid E. coli Detection Project](https://github.com/PubInv/PubInv/blob/master/ideas/Project%20%2341:%20Rapid%20coliform%20presence%20detector.md)

#### protection (COVID-19)

- [GliaX-Faceshield](https://github.com/GliaX/faceshield)
- [GliaX-Noninvasive-Vent](https://github.com/GliaX/noninvasive-vent)

#### ventilator (COVID-19)

- [AmboVent](https://github.com/AmboVent-1690-108/AmboVent)
- [ApolloBVM](https://docs.google.com/document/d/1-DRXnVkJOlDCmvTzh-DgWDxeLSrZTiBYyH0ypzv8tNA/edit)
- [DIY-Beatmungsgerät](https://github.com/DIY-Beatmungsgerat/diy-beatmungsgeraet)
  - refers to [OpenLung](https://gitlab.com/open-source-ventilator/ventilator/OpenLung)
- [Low-Cost Open Source Ventilator or PAPR](https://github.com/jcl5m1/ventilator)
- [OxyGEN](https://github.com/ProtofyTeam/OxyGEN)
- [VentilAid](https://gitlab.com/Urbicum/ventilaid/)
- [Ventmon](https://github.com/PubInv/ventmon-ventilator-inline-test-monitor)

### mobility

- [frachtstück](https://veit-penzenstadler.de/frachtstueck/)
- [roden](https://www.roden.com.ar/product-category/downloads/)
- [OpenEVSE](https://github.com/openevse)

### production tool

#### additive

- [OSE D3D Pro](https://www.opensourceecology.org/d3d-pro/)
- [OSE D3D Universal](https://www.opensourceecology.org/d3d-universal-2/)
- RepRap Family
  - [Hangprinter](https://github.com/tobbelobb/hangprinter)
    - 5 major releases
  - [Mendel90](https://github.com/nophead/Mendel90)
  - [Prusa](https://en.wikipedia.org/wiki/Prusa_i3#History)
    - 7 major releases
  - [RepRap Fisher](https://en.wikipedia.org/wiki/RepRap_Fisher)
  - [RepRap Morgan](https://en.wikipedia.org/wiki/RepRap_Morgan)
    - 4 major releases
  - [RepRap Ormerod](https://en.wikipedia.org/wiki/RepRap_Ormerod)
    - 2 major releases
  - [RepRap Snappy](https://en.wikipedia.org/wiki/RepRap_Snappy)
  - […and others](https://reprap.org/wiki/Build_A_RepRap)
- [NopSCADlib](https://github.com/nophead/NopSCADlib)\
  an OpenSCAD library of parts for 3D printers and enclosures for electronics, etc.

#### cast

- [Extrusion Pro](https://community.preciousplastic.com/academy/build/extrusionpro)
- [ROTOCASTit](https://projects.fablabs.io/@saverio/rotocastit)

#### cutting

- [Lasersaur](https://www.lasersaur.com/)

#### textile

- [OHLOOM](https://wiki.opensourceecology.de/Open_Hardware-Webstuhl_%E2%80%93_OHLOOM)

### tracing & tracking & remote sensing

- [AudioMoth](https://www.openacousticdevices.info/audiomoth)
- [bGeigieNanoKit](https://github.com/Safecast/bGeigieNanoKit)
- [SenseBox](https://sensebox.de/)
  - Open source environmental sensor platform with [open educational resources under CC BY-SA 4.0](https://sensebox.de/en/material)

---

to add after misalignments are clarified:

- [CircuitMess-Ringo](https://github.com/CircuitMess/CircuitMess-Ringo)
  - not OSH yet ([source](https://wiki.opensourceecology.org/wiki/Ringo_Phone))
- [Smill](https://projects.fablabs.io/@eb/smill)
  - license missing
