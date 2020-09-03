# Squashed Meeting Minutes

…of the OSHI working group

## 09-09-2020 – "Welcome to the Next Steps" – Wikimedia, Wikifactory & Fraunhofer IPK

**Invities:**

- Andrés
- Max
- Adam
- Elena
- Sam
- Sonika
- Moe (minutes)

**Agenda:**

First half: API for OSH platforms

- Wikifactory
- data flow:
  - Opem Metadata Repository redundant?

Second half: the Wikibase site of things

- crawler:
  - @WMDE's product manager: to be developed as a Wikimedia extension?
- interface position of the parser:
  - What's within Wikibase's API, what in the Parser's API, what's left out?
  - What will be covered by WMDE?

## 03-09-2020 – "Welcome to the Next Steps" – Wikimedia, Wikifactory & Fraunhofer IPK

**Attendees:**

- Andrés (WF)
- Max (WF)
- Adam (WMDE)
- Elena (WMDE)
- Sam (WMDE)
- Sonika (IPK)
- Moe (IPK) (minutes)

WF … Wikifactory
WMDE … Wikimedia Deutschland
IPK … Fraunhofer IPK

**notes:**

- some smalltalk about Bremen
- introduction to the repository, sharing of updates; find the resources under the following links:
  - repsotitory: <https://github.com/OPEN-NEXT/OSHI>
  - data flow diagramme: <https://github.com/OPEN-NEXT/OSHI/blob/master/README.md#technical-details>
  - current draft of the metadata standard (including the data fields): <https://github.com/OPEN-NEXT/OSHI/blob/master/OSH_metadata.md#classes--slots>
  - requirements for crawler & parser: <https://github.com/OPEN-NEXT/OSHI/blob/master/tmp_requirements-crawler.md>

First half: API for OSH platforms

- data flow:
  - don't use TTL, upload to Wikibase is done by JSON
  - metadata files should use the [JSON-LD](https://json-ld.org/) format
  - ✓ changes included in [28642da](https://github.com/OPEN-NEXT/OSHI/commit/28642da278f4d9c9029a9ebab7b2113a92691577) and [2707eca](https://github.com/OPEN-NEXT/OSHI/commit/2707eca30ba40f2fc528aedbd11af97f632ac857)
  - function of the "Open Metadata Repository" may be covered by crawler, parser and Wikibase API, which would make it redundant → to be assessed until next time
- API (not yet in the data flow diagramme)
  - data source; most data field defined in the current draft of the [metadata standard](https://github.com/OPEN-NEXT/OSHI/blob/master/OSH_metadata.md#classes--slots) are probably already covered in OSH online development environments as WF
  - open API makes this information accessible
  - data is pushed either via the crawler or the parser to Wikibase
  - API module shall be useful for a variaty of OSH platforms; however, WF will be its first 'user'
  - API building will be done by WMDE in cooperation with WF
- WF looks through [data fields]((https://github.com/OPEN-NEXT/OSHI/blob/master/OSH_metadata.md#classes--slots)) and assesses which data fields are already covered by the WF platform and which are not
  - some data field are more important than others; WF & Moe will discuss this in detail in the next meeting; hopefully no (bigger) changes will be required (on any side) :)

Second half: the Wikibase site of things

- Wikibase installation
  - online! accessible under <wikibase.oho.wiki>
  - configuration questions answered!\
    available under <https://pad2.opensourceecology.de/s/Sy8DjWQGv>
- Crawler
  - will be done by IPK
  - may be developed as a Wikimedia extension
    - → to be assessed by WMDE's product manager 'til next time
  - crawling frequency: yet flexible\
    probably once a month; depends how people use & adopt the metadata standard;\
    …of course we're free to crawl more often in phases where we feel the need
    for it, there's no requirement from the project proposal, though
- Parser
  - will be fully or partly done by WMDE
  - exact scope will be assessed 'til next time by @Adam :)
- Ontology\
  (the repository yet just includes a formal description of it)
  - will be done by IPK
  - WMDE will answer questions
    - _first question:_ Are there templates/guidelines/etc. for building an
      ontology that is as compatible as possible to Wikidata?\
      _first answer:_ Nope. People usually just link to Wikidata properties they
      reuse, defining that this property in this local Wikibase instance is the
      same as that Wikidata property

## 09-07-2020 – first metadata draft

**Attendees:**

- Julieta
- Emilio
- Robin
- Moe (minutes)

**notes:**

- Hello, arriving, small talk
- Quick repetition of the scope
- Update: I'll pitch this to OKH this Friday as v2.0 of that standard
- decision about file formats ([issue 4](https://github.com/OPEN-NEXT/OSHI/issues/4))
  - → use TOML only for starters & keep it simple
- decision about file name & location convention ([issue 5](https://github.com/OPEN-NEXT/OSHI/issues/5))
  - → approved
- Looking onto the [scope](Wikibase_Qs.md) and the first [draft](OSH_metadata.md)… does this all make sense? ([issue 2](https://github.com/OPEN-NEXT/OSHI/issues/2))
  - → formulate scope in a much easier way
    - who's the end user?
    - what's problem it solves?
  - → add information about the version of the metadata standard used
- Any idea where we can find function (not _usage_) categories? I wouldn't like to create a category tree from scratch. No one needs that.
  - question for wikidata
  - search through wikipedia
  - ask IEEE
- Gathering sample data:
  - OSH should
    - be well/completely documented
    - have an active community behind it
  - → I'll present these as flagship projects wherever I can
  - Who should I contact/approach?
    - GOSH forum discussion with docubricks
    - DIN SPEC mailing list
    - → upload CSV + open issue linking to this CSV so people know where to add projects
- Someone knows someone from Wikidata who's interested in organising OSH in Wikidata? Would be great to collaborate (also from the OKH side)
  - Who should I contact/approach?
    - thanks @thessaly ! :) (I won't post the names here for privacy reasons)
- Ciao Cacao & have a nice Thursday

## 25-06-2020 – first metadata draft

**Attendees:**

- Robin
- Moe (minutes)

**Notes:**

- ~~Where exactly is new, own vocabulary ontology necessary and where can I just use workarounds & templates for data input?~~
  - → will be checked by Moe in the cooperation with Wikimedia Deutschland
- ~~How does referencing to other DBs work? as e.g. for function categories defined in Wikidata?~~
  - → answered by Wikimedia in a previous meeting
  - we'll squash all the data into one Wikibase instance; this makes life a lot easier; maintenance of different ontology modules or subdatasets is still possible
  - anyway, wikibase offers special features to query other wikibase instances, even to combine different instances into one query; forgot the specific term; the wikimedia community can provide details :)
- Can we trace different versions of OSH with the given metadata? (e.g. crawling URL indicates whether or not OSH is a variant or different version of already existing OSH)
  - ✓ yes, yey
- In a query, can we get the file format from a file link?
  - ✓ yes, yey
- Looking onto the [scope](Wikibase_Qs.md) and the first [draft](OSH_metadata.md)… does this all make sense? ([issue 2](https://github.com/OPEN-NEXT/OSHI/issues/2))
- ✓ yes, yey
- cooperation with Wikimedia Deutschland
  - create initial test data set
    - 50…150 items (instances) by the end of CW 27

## 30-04-2020 – little kickoff

**Attendees:**

- Julieta
- Robin
- Erik
- Moe (minutes)

forgot to invite: Emilio (sorry, Emilio)

**Notes:**

- first draft for DB structure
  - various specified DBs with own onthologies, compatible with each other so that queries across different DBs can be performed
  - DB for OSH-Modules (target for v1.0 of this wikibase instance)
    - = OSH assemblies
    - which consist of
      - other OSH-Modules
      - OSH Components
      - standard parts
      - proprietary parts
  - DB for standard parts (optional target for v1.0)
  - ideas for further DBs:
    - manufacturers (to enable decentralised production of OSH as manufacturer metadata can be mapped over OSH metadata (tolerances, dimensions, material etc.))
    - funding programes (matchmaking between funders and cool projects)
    - scientific publications (e.g. in  cooperation with Journal of Open Hardware)
    - connection to Wikidata (to connect technical documentation with _real_ data :) )
- standards are the backbone of this structure
  - technical documentation: DIN SPEC 3105 & [TsDC](https://gitlab.com/OSEGermany/oh-tsdc/)
  - metadata: Open Know-How manifest v1.0 (+v2.0 (or hard fork) see below ↓)
    - first draft for metadata (and its structure) of OSH [here](OSH%20metadata.md)
    - will be pitched to Open Know-How working group
- we will make use of
  - guidelines & standard modules for onthologies (thanks @Julieta! 🎉)
  - [wbstack.com](wbstack.com) in order to test our onthology approaches

**ToDo:**

- @Moe sends a short project description and mail addresses of the working group to @Julieta, so…
- @Julieta creates an instance using [wbstack.com](wbstack.com)) where we all create accounts, and…
- @Julieta connects us/@Moe to a group of smart people who designed guidelines & standard modules for onthologies (Cristina Sarasua, ETH Zurich)
- @Moe invites everyone to GitHub repo
