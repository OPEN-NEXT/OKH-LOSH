# requirements for crawler & parser

## general

- crawler fills a DB with data
- this DB can also include manual entries
- parser interprets DB data
- …adds more information to it (e.g. from the GitHub API)
- …and translates it into TTL/RDF
- a parser submodule uploads the TTL/RDF to <wikibase.oho.wiki>

## formal requirements

- published under a free/open license
- fully documented following best practices of the FOSS community
- uses existent FOSS modules wherever possible/feasible
- use of existent libraries & modules where possible
  - to integrate ourselves into the local ecosystem
  - to reduce development work
  - to facilitate maintenance
- as maintenance falls to OSEGeV after the project, software and documentation must integrate well into the organisation's infrastructure
  - development on <https://gitlab.com/OSEGermany/>
  - development in compliance with internal guidelines of OSEGeV (usage of docker etc.)
  - documentation in collaboration with representatives from OSEGeV

## crawler

### crawling fundamentals

- crawls for metadata files…
  - OKH manifest files (v1.0)
  - metadata files following [the draft in this repo](OSH_metadata.md) (which will hopefully migrate to OKH as v2.0)
- …on known domains…
  - provided in an extra file (e.g. CSV)
  - file location follows a known pattern but may differ among different domains
- interprets the content
  - parse source & export URLs (see [metadata draft](OSH_metadata.md) for details) for file formats
  - check correctness SPDX license identifier
  - gathers all the information/metadata starting from the OSHM file, which links to the sBoM, which links to POSH files
- adds information from other platforms (e.g. GitHub/Gitlab API)
  - identify forks, versions/releases
  - get number of contributors
- converts this bunch of information into TTL
- …and uploads it to the wikibase instance

### crawling extras

- checks whether links are dead
- does a pre-check of according to DIN SPEC 3105-1 (standard compoents unambiguously referenced? source files available in an original format? export files given? etc.)

## parser

### parsing fundamentals

### parsing extras
