---
title: Ontology Mapping | OKHv1 → OKH-LOSHv1
---

# Notes

The Open Know-How Manifest Specification Version 1.0
([OKHv1](https://standards.internetofproduction.org/pub/okh/release/1))
gave a first approach to organise open source hardware via representative metadata.

Some OSH projects already follow this specification:

- browse through projects here:\
    <https://search.openknowhow.org/>
- find a full list of projects here:\
    <https://github.com/OpenKnowHow/okh-search/blob/master/projects_okhs.csv>

Source for the mapping: [OKHv1 Section 4.5 ff](https://standards.internetofproduction.org/pub/okh#manifest-metadata)

## Specification Diff

| specification | [OKHv1 Section 4](https://standards.internetofproduction.org/pub/okh#specification-for-open-know-how-level-1-discoverable-know-how) | OKH-LOSHv1 |
|---|---|---|
| manifest file format | YAML v1.2 | TOML |
| manifest file name | anything containing "okh" | anything containing "okh", but preferably just `okh.toml` |
| declaration | via `%Open Know-How Manifest 1.0` in line 1, and 3 dashes in line 2 | specification of the version used in the data field `okhv` |

# Data fields

## direct matches

```
"title" = okh:name
"version" = okh:version
"image" = okh:image
"documentation-home" = okh:repo
"documentation_language" = okh:documentationLanguage
"bom" = okh:bom
"archive-download" = okh:release
```

## fields with rules

### date

`date-created`/`date-updated`

```
if
    git-based platform is used
       field is ignored, use git-timestamp from corresponding last commit
elseif
    `date-updated` isempty
        `date-created` = okh:timestamp
else
    `date-updated` = okh:timestamp
```

### derivative of

`derivative-of`/`variant-of`,
see [4.6.15 f. Derivative of](https://standards.internetofproduction.org/pub/okh#derivative-of)

```
if
    "manifest" isempty
        "web" = okh:forkOf
else
    shorten the "manifest" URL to a repo URL and use as okh:repo
```

### description

`description`/`intended-use`/`health-safety-notice`

```
okh:function = "description" + "intended-use" + "health-safety-notice"
```

### development-stage

`development-stage`/`made`/`made-independently`,
see [4.6.11-13 Stage of development - Has been made independently](
https://standards.internetofproduction.org/pub/okh#stage-of-development)

```
if
    "made-independently" = true
        okh:technologyReadinessLevel = otrl:OTRL-3
        okh:documentationReadinessLevel = otrl:ODRL-3
elseif
    "made" = true
        okh:technologyReadinessLevel = otrl:OTRL-3
elseif
    "development-stage" = "prototype"
        okh:technologyReadinessLevel = otrl:OTRL-3
```

These OKHv1 fields can be included as [custom keys](#custom-keys)
regardless of how they were processed here.

### license

`license`, see [4.7.1 License](https://standards.internetofproduction.org/pub/okh#license)

```
if
    "hardware" isnotempty
        if
            "hardware" = SPDX identifier
                "hardware" = okh:spdxLicense
        else
            "hardware" = alternativeLicense
elseif
    "documentation" isnotempty
        if
            "documentation" = SPDX identifier
                "documentation" = okh:spdxLicense
        else
            "documentation" = alternativeLicense
else
    error: no license
```

remaining fields (`documentation` and `software` or only `software`)
may be included as [custom keys](#custom-keys).

### licensor

`licensor`, see [4.7.2 Licensor](https://standards.internetofproduction.org/pub/okh#licensor)

```
"name" = okh:licensor
```

### making instructions

`making-instructions`, see [4.8.7 Assembly Instructions](https://standards.internetofproduction.org/pub/okh#assembly-instructions)

```
"path" = okh:manufacturingInstructions
```

### operating instructions

`operating-instructions`, see [4.8.12 Operating Instructions](https://standards.internetofproduction.org/pub/okh#operating-instructions)

```
"path" = okh:userManual
```

### software

`software`, see [4.8.15 software](https://standards.internetofproduction.org/pub/okh#software)

```
create okh:software
"title" = label of okh:software
"path" = okh:release
```

### standards-used

`standards-used`, see [4.6.14 Standards used](https://standards.internetofproduction.org/pub/okh#standards-used)

```
if
    "reference" isnotempty
        "reference" = okh:standard
elseif
    "standard-title" isnotempty
        "standard-title" = okh:standard
```

The OKHv1 fields can be included as [custom keys](#custom-keys)
regardless of how they were processed here.

### Sub-Thing

`sub`, see [4.6.17 Sub-thing](https://standards.internetofproduction.org/pub/okh#sub-thing)

indicates another MOSH (subassembly) used in this MOSH

```
create sub-MOSH
"title" = okh:name
"manifest" = okh:manifestFile
if
    "manifest" isempty
        "web" = okh:repo
else
    shorten the "manifest" URL to a repo URL and use as okh:repo
```

## Custom Data Fields

The following data fields are either ignored or directly included as custom keys.

- `contact`
- `contributors`
- `design-files`/ `schematics`/ `manufacturing-files`, see [4.8.3 ff. Design Files](https://standards.internetofproduction.org/pub/okh#design-files)
  - sadly their definition/use is too vague/messy to map them directly onto OKHv2,
    however these are still valuable fields
- `development-stage`/`made`/`made-independently` (see [field rules](#development-stage))
- `disposal-instructions`
- `documentation-is-translation`
- `keywords`
- `license` (see [field rules](#license))
  - (`documentation`)
  - `sofware`
- `maintenance-instructions`
- `manifest-author`
- `manifest-is-translation`
- `manifest_language`
- `project-link`
- `quality-instructions`
- `risk-assessment`
- `standards-used` (see [field rules](#standards-used))
- `tool-list`
- `tool-settings`
