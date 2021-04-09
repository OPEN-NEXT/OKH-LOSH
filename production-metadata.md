# Specification for production metadata

## mechanical parts (PRT)

- manufacturing process (multiple)
- material (as specific as reasonable)
- outer dimensions (using openSCAD primitives)
- mass
- smallest tolerance class (according to ISO 286)

## mechanical assemblies (MEC)

- outer dimensions (using openSCAD primitives)
- mass
- smallest tolerance class (according to ISO 286)
- special tools involved
- auxiliary material involved

## welded assemblies (WEL)

- outer dimensions (using openSCAD primitives)
- mass
- welding process (ID from ISO 4063)
- quality level (according to ISO 10042)
- working positions involved (according to ISO 6947)
- filler materials involved (ID from e.g. ISO 544, ISO 2560, ISO 3581)

## PCBs (PCB)

- size
  - e.g. "60x80 cm"
- copper-thickness
- layer-count
- trace-width
- smallest-via
- component-sides
  - 1 or 2
- silkscreen-printing-sides
  - 0, 1 or 2
- solder-mask-sides
  - 0, 1 or 2
- high-tg
  - (glass-transition temperature in °C)
