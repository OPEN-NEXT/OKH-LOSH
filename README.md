[![DOI](https://zenodo.org/badge/259683880.svg)](https://zenodo.org/badge/latestdoi/259683880)
[![GitHub license](https://img.shields.io/github/license/OPEN-NEXT/OKH-LOSH.svg?style=flat)](./LICENSE)

# OKH-LOSH

LOSH: **_A Library of Open Source Hardware - technical documentation in an open graph database._**

demonstrator will be available at [wikibase.oho.wiki](https://wikibase.oho.wiki/)

The work here is based on the [Open Know-How Specification v1.0.0](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#75fb9df0-a7b3-427f-993a-b23fe1c81a58), specifically to make the OKHv1 specification applicable to linked open data and rework data fields after latest research results.\
However, lots of changes have been made so it's hard to still call this a fork.\
After validation this will be proposed to maintainers of the Open Know-How Specification as a new major version of the specification.

## Intro

### Who is doing this?

[OPENNEXT](https://opennext.eu/) is a collaboration
between 19 industry and academic partners
across Europe.
Funded by the [European Union](https://europa.eu/)'s
[Horizon 2020](https://ec.europa.eu/programmes/horizon2020/) programme,
this project seeks to enable small and medium enterprises (SMEs)
to work with consumers, makers, and other communities in rethinking
how products are designed and produced.
[Open source hardware](https://www.oshwa.org/definition/)
is a key enabler of this goal
where the design of a physical product is released with the freedoms
for anyone to study, modify, share, and redistribute copies.
These essential freedoms are based on those of [open source software](https://opensource.org/osd),
which is itself derived from [free software](https://www.gnu.org/philosophy/free-sw.en.html)
where the word free refers to freedom, *not* free-of-charge.
When put in practice,
these freedoms could potentially not only reduce proprietary vendor lock-in,
planned obsolescence, or waste but also stimulate novel –
even disruptive – business models.
The SME partners in OPENNEXT are experimenting
with producing open source hardware and even opening up the development process
to wider community participation.
They produce diverse products ranging from [desks](https://stykka.com/),
[cargo bike modules](http://www.xyzcargo.com/),
to a [digital scientific instrument platform](https://pslab.io/)
(and [more](https://opennext.eu/project-team/#sme)).

The work carried out in this repository is subject to WP3 of OPEN!NEXT
("Supporting production engineering with ICT infrastructure")
and lead by the [department of Information and Process Control
at the Fraunhofer Institute for Production Systems and Design Technology](https://www.ipk.fraunhofer.de/en/about-us/organization/virtual-product-creation.html).

### tl;dr

a distributed database for OSH modules:
a demonstrator for a piece of ICT infrastructure to support design reuse

Standards are the backbone for this approach.

### short & crisp

We are aiming to build the (real) Internet of Things – the Internet of Open Hardware.

## Scope

### tl;dr Q&A

**What is the domain that the ontology will cover?**

Open source hardware modules.\
A "module" is defined here as an assembly with a defined purpose. The scope/size of a module is defined by every project individually. On git-based systems, every repository represents exactly one module (except otherwise noted).

**Who's the enduser you have in mind?**

1. developers\
  the whole thing here is first and foremost about **design reuse**
2. manufacturers / service providers\
  find OSH published under a free/open license (we perform quality checks) so that you can modify, replicate and exploit OSH products however you like e.g. for cases of decentralised (mass) production, maintenance and service provision – or just for yourself.

**What's the problem this thing is solving? Or rather, how does this 'tool' look like?**

1. It's a powerful filter for OSH. Find what you acutally need.
2. It's a knowledge base capable to
  1. answer complex questions like
    "What development platforms are mainly used among OSH projects that got certified by OSHWA or attested according to DIN SPEC 3105-2?";
  2. cross-link information
    (e.g. ongoing research with OSH designs (e.g. in case of COVID-19)).

**What are use cases of the ontology?**

- find the OSH that solves your problem
  (→ **linking OSH modules with functional categories**)
  - filter for license, certificate, functional categories,
    file formats…
  - e.g. search for corona-related projects
- provide portable metadata: OSH can be published on various platforms
- facilitate packaging: essential files can be directly linked in the metadata so:
  - we can run periodic tests to see whether files are still online,
  - you can download those files directly from the LOSH frontend
- RDF & Wikibase enable custom use cases (e.g. for researchers or other OSH platforms) e.g. by writing custom queries or by linking to other data/knowledge bases such as Wikidata

**Who will use and maintain the ontology?**

1. all the awesome communities that provide the ontology modules we are using e.g. SPDX
2. first and foremost: **us**
3. this ontology is yet to be presented to the Open KnowHow Community; they may choose to endorse this approach as Version 2.0.0 of their specification.

### Outlook

**We want to organise open source hardware in a graph database.**

There's a [longlist](Wikibase_Qs.md) of cool use cases of such a knowledge base.
Lots of information (including the technical documentation itself) could be stored as linked open data or simply linked together.

The future could bring e.g.:

- automated quality & completeness checks for the technical documentation
- unambiguous reference of all parts (e.g. to a library of standard components or to other OSH)
- automated matchmaking to manufacturers based on production metadata
- automated matchmaking with suitable finding oppurtunities

## Technical details

**How does the dataflow generally work?**

![dataflow illustration](illustrations/dataflow-principle.svg)

- technical details of the wikibase instance: <https://gitlab.opensourceecology.de/verein/koordination/it/tickets/-/issues/43>
- open standards used:
  - The [DIN SPEC 3105](https://gitlab.com/OSEGermany/OHS)
    (to be published under CC BY-SA 4.0 in June 2020)
    and the [OH-TsDC](https://gitlab.com/OSEGermany/oh-tsdc) define clear,
    enforceable criteria for technical documentation of OSH
    (+ a community-based assessment procedure in order to prove that)
  - The [Open Know-How Metadata Standard](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1)
    gives a first approach to organise OSH through reasonable metadata.

**Can I see the ontology structure somewhere?**

Our CI automatically generates exports from the TTL source. You can find:

- Markdown files laying out the structure,
- GraphViz/DOT graps representing the structure,
- PNG & SVG renders of the graphs

here: <https://open-next.github.io/OKH-LOSH/>

Note that when invalid TTL files are pushed, the CI will give back an error and no exports will be available.

### Related work

- the importer to push the ontology from any git-based instance to any Wikibase instance\
  <https://github.com/hoijui/LOSH-tools> (by hoijui, IPK)
- the reworked API to improve reconciliation tasks\
  <https://github.com/wmde/WikibaseReconcileEdit> (by addshore, WMDE)
- the crawler that collects all the data\
  <https://github.com/OPEN-NEXT/LOSH-krawler> (by ahane, konek.to)

## Want to contribute \[?\]

'til we have a proper conribution guide,
just join our group on [telegram](https://t.me/joinchat/FiYCVhD-NPfpMr5PnZaiNQ) :)

## Why are we doing this?

"Human history, closely explored,
boils down to the history of invention of better tools."\
– Ernst Knapp: cultural geographer (1808-1896)
