# functional description

## fundamentals

- crawls for metadata files…
  - OKH manifest files (v1.0)
  - metadata files following [the draft in this repo](OSH_metadata.md) (which will hopefully migrate to OKH as v2.0)
- …on known domains…
  - provided in an extra file (e.g. CSV)
  - file location follows a known pattern but may differ among different domains
- interprets the content
  - parse source & export URLs (see [metadata draft](OSH_metadata.md) for details) for file formats
  - check correctness SPDX license identifier
  - …
- adds information from other platforms (e.g. GitHub/Gitlab API)
  - identify forks, versions/releases
  - get number of contributors
- converts this bunch of information into TTL
- …and uploads it to the wikibase instance

## extras

- checks whether links are dead
- does a pre-check of according to DIN SPEC 3105-1 (standard compoents unambiguously referenced? source files available in an original format? export files given? etc.)

## formal requirements

- licensed under GPLv3 (any objectives?)
- published on GitHub under the organisation OPEN!NEXT
- fully documented following best practices of the FOSS community
- use of existent libraries & modules where possible
  - to integrate ourselves into the local ecosystem
  - to reduce development work
  - to facilitate maintenance
