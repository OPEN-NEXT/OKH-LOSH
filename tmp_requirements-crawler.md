# functional description

- crawls for metadata files…
  - OKH manifest files (v1.0)
  - metadata files following [the draft in this repo](OSH_metadata.md) (which will hopefully migrate to OKH as v2.0)
- …on known domains…
  - provided in an extra file (e.g. CSV)
  - file location follows a known pattern but may differ among different domains
- …and copies them to a publicly accessible location (git repo, area on [oho.wiki](en.oho.wiki) etc.)

- a script checks links within these metadata files for availability on a regular basis (error 404)

# formal requirements

- licensed under GPLv3
- published on GitHub under the organisation OPEN!NEXT
- fully documented following best practices of the FOSS community
- use of existent libraries & modules where possible
  - to integrate ourselves into the local ecosystem
  - to reduce development work
  - to facilitate maintenance