---
title: Technology Readiness Levels for Open Source Hardware
---

# Notes

- requirements:
  - rapidly assess suitibility of technology for a certain use case & operation environment
    (& easily monitor progress made by the project in this regard)
  - fast & intuitive assessment
    → clear criteria, least possible testing / data akquisition possible
  - Compare very diverse technologies
    (as stated in [this paper](https://ec.europa.eu/isa2/sites/isa/files/technology_readiness_revisited_-_icegov2020.pdf))
    → high abstraction
- derived from [EU-H2020 Annex G](https://ec.europa.eu/research/participants/data/ref/h2020/wp/2014_2015/annexes/h2020-wp1415-annex-g-trl_en.pdf)
  - titles have been copied (partly shortened)
  - …and interpreted for the context of OSH
  - …considering ESA's handbook ([ref](https://artes.esa.int/sites/default/files/TRL_Handbook.pdf))
    and NASA's definitions ([ref](https://www.nasa.gov/pdf/458490main_TRL_Definitions.pdf))

# Principle

<!--- NASA's TRL are too complicated -->

"\[NASA's\] TRLs \[…\] provide useful insights into two key contributors to readiness:

1. degree of functionality provided
2. fidelity of the environment (to the intended operational environment)
   in which this functionality has been demonstrated

([ref](https://apps.dtic.mil/dtic/tr/fulltext/u2/a443149.pdf))

Besides criticism, the TRL approach is chosen as it is well tested and simpler,
thus easier to use.
That stated, the authors found TRL more suitable for a stable,
decentralised application in an open source environment than proposed alternatives
(as e.g. [ref](https://apps.dtic.mil/dtic/tr/fulltext/u2/a443149.pdf)).

It is a special property of open source hardware
that the technology is available for anyone.
Specifically, it is the _technical documentation_ that enables entities
to study/use, make, modify and distribute the technology (ref: DIN SPEC 3105-1).
However, technology readiness can be independent from the state of the documentation.
Hence, two scales are introduced:

1. Technology Readiness Levels for the context of OSH (OTRL)
2. Documentation Readiness Levels for the context of OSH (ODRL)

Both will be provided as text and RDF document
to ensure equally human and machine readability.

# Concept

## OTRL

### General

Resources:

- https://motius.de/phasen-der-produktentwicklung/#produktentwicklung-phase-4-das-minimum-viable-product-mvp
- https://de.wikipedia.org/wiki/Produktentwicklung#Ablauf
- https://doi.org/10.1007/978-3-662-57303-7
- VDI 2220

|OTRL|Stage|Goal|
|---|---|---|
|OTRL 1|ideation|product specifications/requirements|
|OTRL 2|conception|proof of concept|
|OTRL 3|technical design|early prototype|
|OTRL 4|product design|minimum viable product|
|OTRL 5|safe product|CE certification|

<!--- ToDo:

1. getting requirements ready
2. finding a solution concept
3. translate solution conecpt into a physical hardware solution
4. design a product that a) reliably covers core features and b) can be built, modified and operated by non-contrbutors
5. finish all relevant tests for CE certification

-->

### OTRL 1

`basic principles observed`

Potential has been identified and formulated:
Knowledge generated underpinning hardware technology concepts/applications.

### OTRL 2

`technology concept formulated`

Concept and potential usefulness has been ellaborated and formulated:
Invention begins, practical application is identified but is speculative,
no experimental proof (e.g. a physical prototype) or detailed analysis is available
yet to support the conjecture.

### OTRL 3

`experimental proof of concept`

Key functions of the concept are tested & proven in a controlled environment
(e.g. laboratory or just analytical).

### OTRL 4

`technology validated in lab`

A low fidelity application (early prototype, breadboard) was built and operated
in a controlled environment (e.g. laboratory)
demonstrating basic functionality and critical test environments;
performance predictions are formulated towards the final operating environment.

### OTRL 5

`technology validated in relevant environment`

A medium fidelity application (prototype) was built and operated
in a (simulated) realistic operational environment
demonstrating overall performance in critical areas.

### OTRL 6

`technology demonstrated in relevant environment`

A high fidelity application (final version) was built
and operated in a realistic operational environment demonstrating its performance
in the actual operational environment.

At this point the OSH can be deemed "ready for manufacturing"
and the target group can safely exercise the 4 rights of open source
in the operation environment.

### OTRL 7

`system prototype demonstration in operational environment`

OTRL 7 "is a significant but optional maturation step beyond TRL 6,
requiring an actual system prototype demonstration in the expected operational environment.
[…] The driving purpose for achieving this level of maturity
must be tied to assuring system engineering and development management confidence
(more than for purposes of technology R&D).
Therefore, the demonstration must be of a prototype of an actual planned application.
Of course, not all technologies in all systems must be demonstrated at this level"
([ref, p.23](https://artes.esa.int/sites/default/files/TRL_Handbook.pdf)).
It applies for critical or very complex systems (e.g. MRI scanners).

At this point the OSH can be deemed "ready for manufacturing"
and the target group can safely exercise the 4 rights of open source
in the operation environment.

NOTE:
"Implementing TRL 7 has seldom been done in past technology development programs
because it is seldom necessary.
Typically, a TRL 7 demonstration is only implemented in cases of high technical risk
and/or when systems-level innovation is necessary to achieve mission goals and objectives."
([ref, p.23](https://artes.esa.int/sites/default/files/TRL_Handbook.pdf))

EXAMPLE:
A control unit for an open source MRI scanner has been built and tested
in the MRI scanner to reach OTRL 6,
but not regarding the influence and feedback from other,
simultaniously operating modules in the scanner during operation.
This is to be tested to reach OTRL 7.

### OTRL 8

`system complete and qualified`

Hardware, in its final version,
has been built and operated in the intended operational environment
and proven its performance.
It is (theoretically) ready to be sold as a commercial product in the EU.

### OTRL 9

`actual system proven in operational environment`

The hardware is successfully applied by independent entities
in the operational environment.

EXAMPLE: Product is sold in the EU.

## ODRL

### General

It is the complete technical documentation,
published under a free/open license,
that differentiates open source hardware from proprietary hardware.

This "completeness" has been divided into the following 5 levels as shown in table @tbl:odrl-overview.
A detailled description of these levels can be found in the following chapters.

|ODRL|Name|Goal|
|---|---|---|
|ODRL 1|documentation started & accessible|making information available as free/open source material|
|ODRL 2|minimal documentation|enabling usability of the documentation by the provision of essential files and information|
|ODRL 3|full documentation|full exploitability of the documentation|
|ODRL 4|audited documentation|attested compliance with DIN SPEC 3105-1|
|ODRL 5|audited documentation including CE certification documents|enabling decentralised commercial distribution|

: Overview on ODRLs {#tbl:odrl-overview}

<!--- ToDo: read & check --->

<!-- For ODRL documentation requirements after DIN SPEC 3105-1 apply ([ref to chapter](TODO)),
meaning that it must be published under a free/open license and publicly accessible.

By default, experts skilled in the corresponding field of technology
are the target group of the documentation
and hence shall be able to understand the documentation.
However, projects can define other target groups
e.g. by adding layers of abstraction to the documentation ([ref to chapter](TODO)).

It's the technical documentation
enabling the target group to exercise the 4 rights of open source:
to study, to modify, to make and to distribute the documentation or hardware
based on that documentation ([ref to chapter](TODO)). -->

### ODRL 1

`documentation started & accessible`

**IN SHORT:** By OSHWA-compliant licensing terms, free rights of any use are granted to the general public,\
**BUT** not executable due to missing files and information;

**ENABLING** the (legal) use of published information as free/open source material.

**THIS INCLUDES:**

- a free/open license compliant to the OSHWA definition;
- that all legal information (author(s), title, legal code of the license) is available and
- distributed with an unambiguous reference to the specific published documentation (e.g. by the use of git tags for releases).

<!---

`basic information available`

Documentation describes basic characteristics of the hardware
(such as operations-oriented metrics (mass, energy input etc.),
the (expected) operational environment(s) or its function)
or its concept (depending on the OTRL).

Target group understands, what the OSH is,
but not how it works or how it is operated
and hence cannot yet exercise the 4 rights of open source

-->

### ODRL 2

`minimal documentation`

**IN SHORT:** All essential source files are published in appropriate formats,\
**BUT** what "essential" means or "appropriate formats" is subject to the decision of maintainers only – documentation is not finished yet;

**ENABLING** the _practical execution_ of free rights of any use;

**THIS INCLUDES:**

- that information shall be provided in such a way that allows for 1) lossless information distribution (compared to the original development) for modification, 2) without raising the need of proprietary software to study the information;
  - specifically for 3D modelling this means in practice that a CAD file shall be distributed 1) in its native file format 2) alongside with an exported copy in an exchange format (e.g. STEP).

<!-- `drafty documentation`

documentation in progess – aims to describe how the hardware works
and how it is operated, but is partly patchy and/or outdated;
yet too less to exercise the 4 rights of open source -->

### ODRL 3

`full documentation`

**IN SHORT:** Documentation has been completed and deemed fully compliant with DIN SPEC 3105-1,\
**BUT** only by self-assessment by maintainers of the project.

**ENABLING** the full exploitation of the piece of open source hardware, theoretically.

**THIS INCLUDES:**

- xxx.

<!-- `early release`

Target group struggles; execution of the 4 rights of open source is possible,
but only with lots of reconciliation with originators
since the documentation yet lacks fundamental information -->

### ODRL 4

`audited documentation`

**IN SHORT:** Documentation has been attested to be fully compliant with DIN SPEC 3105-1 in a community-based process according to DIN SPEC 3105-2,\
**BUT** yet documentation relevant for CE certification is missing;

**ENABLING** a trustworthy full exploitation of the piece of open source hardware.

**THIS INCLUDES:**

- an attestation from a confirmity assessment body according to DIN SPEC 3105-2 (or equivalent proofs of conformity as e.g. through an OSHWA certification or a RYF certification).

<!-- `relevant release`

target group understands; execution of the 4 rights of open source is possible,
but still requires few reconciliation with originators
since the documentation yet lacks minor information -->

### ODRL 5

`audited documentation including CE certification documents`

**IN SHORT:** Documentation has been attested following DIN SPEC 3105-2 and includes all documentation relevant for CE certification

**ENABLING** decentralised commercial distribution of the piece of open source hardware.

**THIS INCLUDES:**

- xxx.

<!-- `mature release`

target group acts autonomously;
independent entity made the hardware with no reconciliation with originators -->
