OSHI
=

**_The Open Source Hardware Internet - technical documentation in an open graph database._**

# Intro

## tl;dr

connecting open source hardware modules in a graph database – the ICT infrastructure for community-based innovation and circular economy

## long

Some very special advantages of open source technologies only come to effect when we start to connect them. Especially hardware. 

Through open source hardware (OSH) we can share design files, assembly instructions, operation and maintenance guides, recycling guidelines, structural analyses, calculations & simulations etc. – and attached to OSH modules they become as modular as the hardware itself. 

Just as developer can re-use design files to avoid reinventing the wheel, they can re-use documentation of any kind. Applied to calculations, developer could access the cumulated experience of countless OSH modules that have been realised and tested in practise and hence assess e.g. boundary conditions or the dimension of certain components much faster and on a much more reliable basis. What once was the undisclosed know-how of large, specialised enterprises can become a public pool of knowledge.

**We want to organise open source hardware in a graph database.**

There's a [longlist](Wikibase_Qs.md) of interesting information that could be derived from such a database (also regarding compatibility between OSH modules).

For version 1.0 we will focus on hardware only. Ideas for later, compatible databases are:
- standard parts
- calculation tables & machine-readable standards (e.g. regarding welding parameters)
- manufacturers (to match e.g. design requirements with suitable manufacturing lines nearby)
- funding opportunities (to match e.g. funding requirements with OSH projects)

Standards are the backbone for this approach.

## short & crisp

We are aiming to build the (real) Internet of Things – the Internet of Open Hardware.

# Technical details

- backend: wikibase
  - version x.x.x
  - used onthology modules
    - xxx
    - xxx
    - …
- frontend: The Open Hardware Observatory ([oho.wiki](en.oho.wiki)) (=wikimedia extension)
- open standards used:
  - The [DIN SPEC 3105](https://gitlab.com/OSEGermany/OHS) (to be published under CC BY-SA 4.0 in June 2020) and the [OH-TsDC](https://gitlab.com/OSEGermany/oh-tsdc) define clear, enforceable criteria for technical documentation of OSH (+ a community-based assessment procedure in order to prove that)
  - The [Open Know-How Metadata Standard](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1) gives a first approach to organise OSH through reasonable metadata.

# Want to contribute?

'til we have a proper conribution guide,
just send me a quick message via [telegram](https://t.me/moedn) :)
