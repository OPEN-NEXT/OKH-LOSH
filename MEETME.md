<!--
SPDX-FileCopyrightText: 2020 - 2021 Robin Vobruba <hoijui.quaero@gmail.com>
SPDX-FileCopyrightText: 2020 Martin Häuer <martin.haeuer@ose-germany.de>
SPDX-FileCopyrightText: 2020 juli arancio <jarancio@protonmail.com>

SPDX-License-Identifier: GPL-3.0-or-later
-->

# Squashed Meeting Minutes

…of the OSHI working group

## 14-09-2020 – "Welcome to the Next Steps" – Wikimedia, Wikifactory & Fraunhofer IPK

These meeting minutes are omitted due to privacy policies of official project partners.
Find them [here](https://tubcloud.tu-berlin.de/s/SdeJ4neMMzDJeNr/download?path=%2F02_Meetings%2F01_Work%20Package%20Meetings%2FWP3&files=%5BT3.3%5D%20running%20minutes.md).
Please send a request to <assessmen@oho.wiki>
so we can share the requested minutes directly to you.

## 03-09-2020 – "Welcome to the Next Steps" – Wikimedia, Wikifactory & Fraunhofer IPK

These meeting minutes are omitted due to privacy policies of official project partners.
Find them [here](https://tubcloud.tu-berlin.de/s/SdeJ4neMMzDJeNr/download?path=%2F02_Meetings%2F01_Work%20Package%20Meetings%2FWP3&files=%5BT3.3%5D%20running%20minutes.md).
Please send a request to <assessmen@oho.wiki>
so we can share the requested minutes directly to you.

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
- Looking onto the [scope](Wikibase_Qs.md) and the first [draft](OSH_metadata.md)…
  does this all make sense? ([issue 2](https://github.com/OPEN-NEXT/OSHI/issues/2))
  - → formulate scope in a much easier way
    - who's the end user?
    - what's problem it solves?
  - → add information about the version of the metadata standard used
- Any idea where we can find function (not _usage_) categories?
  I wouldn't like to create a category tree from scratch. No one needs that.
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
- Someone knows someone from Wikidata who's interested in organising OSH in Wikidata?
  Would be great to collaborate (also from the OKH side)
  - Who should I contact/approach?
    - thanks @thessaly ! :) (I won't post the names here for privacy reasons)
- Ciao Cacao & have a nice Thursday

## 25-06-2020 – first metadata draft

**Attendees:**

- Robin
- Moe (minutes)

**Notes:**

- ~~Where exactly is new, own vocabulary ontology necessary
  and where can I just use workarounds & templates for data input?~~
  - → will be checked by Moe in the cooperation with Wikimedia Deutschland
- ~~How does referencing to other DBs work?
  as e.g. for function categories defined in Wikidata?~~
  - → answered by Wikimedia in a previous meeting
  - we'll squash all the data into one Wikibase instance;
    this makes life a lot easier;
    maintenance of different ontology modules or subdatasets is still possible
  - anyway, wikibase offers special features to query other wikibase instances,
    even to combine different instances into one query; forgot the specific term;
    the wikimedia community can provide details :)
- Can we trace different versions of OSH with the given metadata?
  (e.g. crawling URL indicates whether or not OSH is a variant
  or different version of already existing OSH)
  - ✓ yes, yey
- In a query, can we get the file format from a file link?
  - ✓ yes, yey
- Looking onto the [scope](Wikibase_Qs.md) and the first [draft](OSH_metadata.md)…
  does this all make sense? ([issue 2](https://github.com/OPEN-NEXT/OSHI/issues/2))
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
  - various specified DBs with own onthologies,
    compatible with each other so that queries across different DBs can be performed
  - DB for OSH-Modules (target for v1.0 of this wikibase instance)
    - = OSH assemblies
    - which consist of
      - other OSH-Modules
      - OSH Components
      - standard parts
      - proprietary parts
  - DB for standard parts (optional target for v1.0)
  - ideas for further DBs:
    - manufacturers (to enable decentralised production of OSH
      as manufacturer metadata can be mapped over OSH metadata
      (tolerances, dimensions, material etc.))
    - funding programes (matchmaking between funders and cool projects)
    - scientific publications (e.g. in  cooperation with Journal of Open Hardware)
    - connection to Wikidata
      (to connect technical documentation with _real_ data :) )
- standards are the backbone of this structure
  - technical documentation: DIN SPEC 3105 & [TsDC](https://gitlab.com/OSEGermany/oh-tsdc/)
  - metadata: Open Know-How manifest v1.0 (+v2.0 (or hard fork) see below ↓)
    - first draft for metadata (and its structure) of OSH [here](OSH%20metadata.md)
    - will be pitched to Open Know-How working group
- we will make use of
  - guidelines & standard modules for onthologies (thanks @Julieta! 🎉)
  - [wbstack.com](wbstack.com) in order to test our onthology approaches

**ToDo:**

- @Moe sends a short project description and mail addresses of the working group
  to @Julieta, so…
- @Julieta creates an instance using [wbstack.com](wbstack.com))
  where we all create accounts, and…
- @Julieta connects us/@Moe to a group of smart people
  who designed guidelines & standard modules for onthologies
  (Cristina Sarasua, ETH Zurich)
- @Moe invites everyone to GitHub repo
