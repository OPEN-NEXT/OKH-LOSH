---
title: Wikibase Frontend Specifications
subtitle: for the Library of Open Source Hardware (LOSH)
command: pandoc Wikibase-Frontend-Specifications.md -o Wikibase-Frontend-Specifications.pdf --toc --pdf-engine=xelatex -V documentclass=report
...

# Intro

On LOSH you can

1. **search OSH & filter results** (LOSH's main purpose is to facilitate design reuse),
2. access templates & guides to get your OSH project listed (which is easier than it sounds),
3. access data directly (via Wikibase or RDF),
4. suggest new features (via issues on GitHub),
5. buttons

# Target Group

In descending order of priority:

1. OSH developer (e.g. maker) or anyone else looking for either specific OSH solutions or inspiration one's own project;
2. Researcher or anyone else who wants to get an overview of the OSH ecosystem;
3. Companies or other producing entities looking for OSH to manufacture and sell.

# Functions

The main goal is to provide a frontend for the Wikibase instance in such a way that allows an average maker (hence someone not skilled or familiar in the use of Wikibase or RDF) to intuitively access & explore LOSH's data and use all other subsequently described functions of the LOSH.
It also should have an appealing design, so people don't get shocked off by a design that reminds them on PHP forums from the '90s.
We'll continiue using and promoting this platform long after OPEN!NEXT has ended.

Functions in the frontend include but are not limited to:

- a prominent searchbar for free text search (presumingly searching the metadata fields `function` and `name`)
- in the search, applying combinable filters, based on the metadata specification of LOSH, e.g. for:
  - license (and license categories),
  - documentation language,
  - file formats (and file format categories),
  - patent class (and representative labels for the same)
    - equals a 'function category'
  - TsDC-ID (and representative labels for the same)
    - equals a 'production category'
  - OTRL (and representative labels for the same)
    - …to filter for specific readiness levels of the design &/ the documentation
- input of free-form SPARQL queries to query
  - Wikibase
  - the RDF knowledge base, published in a git repository
- 'threading' of versions/variants of the same OSH
- compare search results by selected data fields
- detail pages for OSH projects (displayed e.g. after clicking on a search result) containing e.g.:
  - metadata completeness (=extent to which the specification has been complied; also indicating the completeness of documentation)
  - data source
  - name
  - version + timestamp
  - repo URL
  - image
  - licensor, owner, organisation
  - license
  - functional description
  - number of contributors
  - list & number of self-designed parts
  - URLs to source & export files (including BoM and manuals)
  - production metadata (yet to be processed from [here](MAKER-INPUT-production-metadata.md))
- data export (download), of e.g.:
  - all design files known from the metadata
  - search results in various formats (e.g. CSV, JSON)
- interactive elements, such as:
  - reporting an issue
    - regarding the data set (“Report faulty/missing data”)\
      → goes to LOSH's git repository
    - regarding the hardware &/ the documentation\
      → goes to the repository of the OSH
  - rating (e.g. 1…5 stars) or 'starring' (like on GitHub)
  - additional features to be defined in reconcilitation with the UX team
  - Button on detail pages: "I built this hardware" (maybe a scale ↓)
    - …but didn't succeed, documentation is incomplete/faulty
    - …with lots of help from the originators
    - …(almost) independently, great documentation!
    - → count is saved on wikibase
  - Suggest for certification / community-based assessment at
    - [OSHWA](https://application.oshwa.org/apply)
    - [OSE Germany – Confirmity Assessment Body according to DIN SPEC 3105-2](https://gitlab.opensourceecology.de/verein/projekte/cab/CAB)
    - [OHO – Confirmity Assessment Body according to DIN SPEC 3105-2](https://en.oho.wiki/)
- tools & guides to get one's OSH listed on the LOSH:
  - UI for the generation of metadata files from user entered metadata values to upload on a supported git-based platform (either to own repository or to LOSH's collection point)
  - embedding Wikifactory's Source&Export tool to upload projects from and to supported platforms

These functions form a preliminary scope for the frontend.
As in every research project, this scope and lots of corresponding details are to be iteratively refined.\
Hence, direct contact and regular technical meetings with engineers/developers would be ideal.

Development of the frontend will be carried out as a free/open source software (FOSS) project and therefor shall respect and comply with best practices from the FOSS community, specifically:

- source code will be published under [GPLv3](https://www.gnu.org/licenses/gpl-3.0-standalone.html) on a git-based online platform such as GitLab or GitHub alongside with
- corresponding documentation, which follows community best practices and enables reuse of the source code, which itself
- respects this principle and prefers reusing existing FOSS modules over hardcoded elements where feasible.

# Examples

- <https://certification.oshwa.org/list.html>
  - pretty basic interface allowing for free text search (name and functional description) and filtering for categories and licenses
  - list view allows fast comparism of the results by the displayed data columns
  - source code published [here](https://github.com/oshwa/oshwa-certification)
- <https://search.openknowhow.org/>
  - pretty basic interface, it's limited to the use of the search bar
  - gallery view of search results allows easy & fast pre-assessment of the results
  - source code published [here](https://github.com/OpenKnowHow/okh-search)
  - the database relies on metadata following the [OKH specification](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1), hence small YAML files in git repositories → so that comes pretty close to our scenario even though they neither use a crawler nor Linked Open Data
- <https://en.oho.wiki/wiki/Home>
  - more advanced interface, already bringing in some features like filtering or discussions (see the peer-review-based 'certification' they offer)
  - gallery view of search results allows easy & fast pre-assessment of the results
  - mediawiki-based platform
  - source code published [here](https://gitlab.opensourceecology.de/verein/projekte/oho/oho-legacy)
  - SQL database in the backend and lots of hardcoded elements (such as the category system)

