# OSH Module

= assembly of components with clear input, output and interfaces

- name or working title
- version
    - of hardware design
    - of documentation
- link to documentation release
- authors
- license
- functional description (e.g. what functions it is supposed to deliver, what is the problem it solves, for whom etc.)
    - → use guidelines for naming convention e.g. [as for inventions](https://www.wipo.int/export/sites/www/standards/en/pdf/03-15-01.pdf)
- applying technology-specific documentation criteria (TsDC-IDs)
- link to [standardised BoM](#standardised-bom)
- (physical specifications?)

## standardised BoM

= for documentation purposes; easy to read, crawl and use; maybe call **meta-BoM**?

| Pos. | Name         | Units | Type           | Reference                                |
|------|--------------|-------|----------------|------------------------------------------|
| 1    | casing       | 2     | OSH Component  | link to manifest file (for components)   |
| 2    | screw        | 4     | standard part  | standard designation                     |
| 3    | gear box     | 1     | OSH Module     | link to manifest file (for modules)      |
| 4    | Raspberry Pi | 1     | purchased part | unambiguous reference (not standardised) |

## OSH components

- name or working title
- version
    - of hardware design
    - of documentation
- authors
- license
- link to design files
    - 3D model
        - source → script gets file format
        - export (STD)
    - 2D drawing
        - source → script gets file format
        - export (PDF)
- (link to) functional metadata ← _very_ technology-specific! not to be standardised here
    - dimensions
    - material
    - weight
    - RPM
    - …
