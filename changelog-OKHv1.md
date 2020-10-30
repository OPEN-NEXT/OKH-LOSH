# From OKHv1 to OKHv2

The Open Know-How Manifest Specification Version 1.0
([OKHv1](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1))
gave a first approach to organise open source hardware via representative metadata.

In the following only differences will be noted & explained.

## Specifications

|specification|[OKHv1 Section 4](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#e5a867ac-034f-4e91-aa20-32bb75143b47)|OKHv2|
|---|---|---|
||one manifest file per "version of the thing"|one manifest file per [documentation release](https://gitlab.com/OSEGermany/OHS/-/blob/ohs/DIN_SPEC_3105-1.md#39-documentation-release)|
|file format|YAML v1.2|JSON|
|file name|anything containing "okh"|for MOSH: okh.json; for POSH: anything containing "okh"|
|declaration|via `%Open Know-How Manifest 1.0` in line 1 and 3 dashes in line 2|specification of the version used in the data field `okhv`|
|absolute / relative paths| both allowed|absolute paths only|
|location of the manifest|root directory|MOSH: root directory; POSH: anywhere in the same repository|

## Data fields

NOTE: How to deal with duplicate entries (as for e.g. `function`); example case:

- A manifest file of OKHv1 is found.
  - It contains entries for `description`, `intended-use` and `health-safety-notice`.
- The parser shall map it onto OKHv2 now.
  - The named entries are all referenced to `function` (OKHv2) in the table below.
  - Hence all entries add up to a squashed entry for `function`.

| [OKHv1 Section 4.5 ff](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6) | OKHv2             | Comment                                                                                          |
|---------------------------------------------------------------------------------------------------------------------------------------------|-------------------|--------------------------------------------------------------------------------------------------|
| date-created                                                                                                                                | -                 |                                                                                                  |
| date-updated                                                                                                                                | -                 |                                                                                                  |
| manifest-author                                                                                                                             | -                 |                                                                                                  |
| title                                                                                                                                       | name              |                                                                                                  |
| description                                                                                                                                 | function          |                                                                                                  |
| indended-use                                                                                                                                | function          |                                                                                                  |
| keywords                                                                                                                                    | -                 |                                                                                                  |
| Project Homepage                                                                                                                            | -                 |                                                                                                  |
| health-safety-notice                                                                                                                        | function          |                                                                                                  |
| contact                                                                                                                                     | -                 |                                                                                                  |
| contributors                                                                                                                                | -                 | the wikibase instance may include contributor data, but not from manually created manifest files |
| image                                                                                                                                       | image             |                                                                                                  |
| version                                                                                                                                     | version           |                                                                                                  |
| development-stage                                                                                                                           | development-stage |                                                                                                  |
