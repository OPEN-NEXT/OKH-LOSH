# requirements for Collector and Wikibase-API

## general

Following the [data flow illustration](illustrations/dataflow-principle.svg):

- Collector gets metadata from OSH platform APIs
  - this requires API-specific modules in the Collector software
  - manually createad metadata files are possible for GitHub/GitLab and can be found calling the GitHub/GitLab API
- Collector submits data to Wikibase-API which is the data entry point for the instance under <wikibase.oho.wiki>

## formal requirements

- published under a free/open license
- fully documented following best practices of the FOSS community
- uses existent FOSS modules wherever possible/feasible
  - to integrate ourselves into the local ecosystem
  - to reduce development work
  - to facilitate maintenance
- as maintenance falls to OSEGeV after the project, software and documentation
  must integrate well into the organisation's infrastructure
  - development & documentation in collaboration with representatives from OSEGeV

## functional requirements

### Collector

- framework for API-specific modules
  - find the API selection in [#9](https://github.com/OPEN-NEXT/LOSH/issues/9)
  - consider that the ontology is updatable;
    please consider the maintenance effort
- translates OKHv1 files into OKHv2
  - find conversion table [here](changelog-OKHv1.md)
  - information loss is known and accepted
- converts data (YAML/JSON, CSV) into a transmittable format
  (currently: JSON-LD according to the ontology in this repo);
  data is partly 'interpreted'
  - `sBoM.csv` is to be converted into JSON
  - file formats are obtained from the URLs
  - judging from the file formats, files are automatically sorted into source & export files
- …and submits it to the (already existent) [Wikibase-API](#wikibase-api)
  - <https://www.wikidata.org/w/api.php?action=help&modules=wbeditentity>
  - <https://www.wikidata.org/w/api.php?action=help&modules=wbgetentities>
  - <https://www.wikidata.org/w/api.php?action=help&modules=wbsearchentities>
- crawler must be able to automatically run on OSEG servers, so please also consider the cron!
  - always performs a 'complete crawling';
    filtering is done in reconciliation with the Wikibase-API
- MOSH identification
  - identify versions and hard forks of a MOSH
  - filter/remove forks that have the intention to be merged back into the original MOSH\
    (can live on different platforms, e.g. original on Wikifactory, fork on GitHub)

optional:

- checks whether links _inside_ the metadata files are dead
- checks for typos in manually created metadata files
- more submodules as listed in [#9](https://github.com/OPEN-NEXT/LOSH/issues/9)

### Wikibase-API

1. [x] basic, straight forward data submission (import)
2. [x] data export
   1. whole DB (in Wikibase-flavored RDF)
   2. are query results exportable? As RDF and also a human readable format?
      (as for just saving search results etc.)\
      there's a list of supported file formats
3. [ ] data update
   1. incremental entry adding (filter duplicates; avoids recreating the whole DB with each crawling by checking the DB for
    existing entries and updates)
   2. [Query] mark MOSHs that couldn't be found anymore as 'lost'\
      → do _not_ delete them! deletion can (possibly) happen on Wikibase using queries
4. Ontology bridge (TTL on GitHub → Wikibase)
5. optional: Query bridge (queries on GitHub → Wikibase)
