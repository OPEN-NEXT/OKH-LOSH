# Specification for production metadata

## mechanical parts (COM-MAN)

- manufacturing process (multiple)
- material (as specific as reasonable)
- outer dimensions (using openSCAD primitives)
- smallest tolerance class (according to ISO 286)

## mechanical assemblies (ASM-MEC)

- outer dimensions (using openSCAD primitives)
- smallest tolerance class (according to ISO 286)
- …[copy from TsDC]

## welded assemblies (ASM-WEL)

- …[copy from TsDC]

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
