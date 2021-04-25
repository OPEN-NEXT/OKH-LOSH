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

"\[NASA's\] TRLs \[…\] provide useful insights into two key contributors to readiness:

1. degree of functionality provided
2. fidelity of the environment (to the intended operational environment)
   in which this functionality has been demonstrated

([ref](https://apps.dtic.mil/dtic/tr/fulltext/u2/a443149.pdf))

Besides criticism the TRL approach is chosen as it is well tested and simpler,
thus easier to use.
That stated the authors found TRL more suitable for a stable,
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

|OTRL|Detail|Characteristic|
|---|---|---|
|OTRL 1|basic principles observed|rough idea|
|OTRL 2|technology concept formulated|concept ready|
|OTRL 3|experimental proof of concept|concept is validated in tests|
|OTRL 4|technology validated in lab|early prototype|
|OTRL 5|technology validated in relevant environment|mature prototype|
|OTRL 6|technology demonstrated in relevant environment|ready-to-use product|
|OTRL 7|system prototype demonstration in operational environment|ready-to-use product (for critical or complex applications)|
|OTRL 8|system complete and qualified|finished product (could be sold in the EU)|
|OTRL 9|actual system proven in operational environment|established product|

|ODRL|Detail|Characteristic|
|---|---|---|
|ODRL 0|no documentation available|or noncompliant license|
|ODRL 1|basic information available|know that the OSH is, but not more|
|ODRL 2|drafty documentation|documentation in progress, yet patchy|
|ODRL 3|early release|lots of reconciliation required to build & operate the OSH|
|ODRL 4|relevant realease|few reconciliation required to build & operate the OSH|
|ODRL 5|mature realease|no reconciliation required to build & operate the OSH|

## OTRL

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

For ODRL documentation requirements after DIN SPEC 3105-1 apply ([ref to chapter](TODO)),
meaning that it must be published under a free/open license and publicly accessible.

By default, experts skilled in the corresponding field of technology
are the target group of the documentation
and hence shall be able to understand the documentation.
However, projects can define other target groups
e.g. by adding layers of abstraction to the documentation ([ref to chapter](TODO)).

It's the technical documentation
enabling the target group to exercise the 4 rights of open source:
to study, to modify, to make and to distribute the documentation or hardware
based on that documentation ([ref to chapter](TODO)).

### ODRL 0

`no documentation available`

Documentation is not existent, not publicly accessible
or its license is not compliant with terms stated by the OSHWA Definition 1.0 ([ref](TODO)).

### ODRL 1

`basic information available`

Documentation describes basic characteristics of the hardware
(such as operations-oriented metrics (mass, energy input etc.),
the (expected) operational environment(s) or its function)
or its concept (depending on the OTRL).

Target group understands, what the OSH is,
but not how it works or how it is operated
and hence cannot yet exercise the 4 rights of open source

### ODRL 2

`drafty documentation`

documentation in progess – aims to describe how the hardware works
and how it is operated, but is partly patchy and/or outdated;
yet too less to exercise the 4 rights of open source

### ODRL 3

`early release`

Target group struggles; execution of the 4 rights of open source is possible,
but only with lots of reconciliation with originators
since the documentation yet lacks fundamental information

### ODRL 4

`relevant release`

target group understands; execution of the 4 rights of open source is possible,
but still requires few reconciliation with originators
since the documentation yet lacks minor information

### ODRL 5

`mature release`

target group acts autonomously;
independent entity made the hardware with no reconciliation with originators
