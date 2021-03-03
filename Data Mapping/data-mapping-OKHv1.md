---
title: Ontology Mapping | OKHv1 → OKHv2
---

# Notes

The Open Know-How Manifest Specification Version 1.0 ([OKHv1](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1)) gave a first approach to organise open source hardware via representative metadata.

Some OSH projects already follow this specification:

- browse through projects here:\
    <https://search.openknowhow.org/>
- find a full list of projects here:\
    <https://github.com/OpenKnowHow/okh-search/blob/master/projects_okhs.csv>

Source for the mapping: [OKHv1 Section 4.5 ff](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

## Specification Diff

| specification | [OKHv1 Section 4](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#e5a867ac-034f-4e91-aa20-32bb75143b47) | OKHv2 |
|---|---|---|
| manifest file format | YAML v1.2 | TOML |
| manifest file name | anything containing "okh" | anything containing "okh", but preferably just `okh.toml` |
| declaration | via `%Open Know-How Manifest 1.0` in line 1 and 3 dashes in line 2 | specification of the version used in the data field `okhv` |

# Data fields

## direct matches

```
"title" = okh:name
"version" = okh:version
"image" = okh:image
"documentation-home" = okh:repo
"documentation_language" = okh:documentationLanguage
"bom" = okh:bom
```

##  fields with rules

### archive download

`archive-download`, see [4.8.2 Documentation archive](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

```
"path" = okh:release
```

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

`derivative-of`/`variant-of`, see [4.6.15 f. Derivative of](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

```
if
    "manifest" isempty
        "web" = okh:repo
else
    shorten the "manifest" URL to a repo URL and use as okh:repo
```

### description

`description`/`indended-use`/`health-safety-notice`

```
okh:function = "description" + "intended-use" + "health-safety-notice"
```

### development-stage

`development-stage`/`made`/`made-independently`, see [4.6.11-13 Stage of development - Has been made independently](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

```
if
    "made-independently" = true
        okh:technologyReadinessLevel = otlr:OTLR-5
elseif
    "made" = true
        okh:technologyReadinessLevel = otlr:OTLR-4
elseif
    "development-stage" = "prototype"
        okh:technologyReadinessLevel = otlr:OTLR-4
```

These OKHv1 fields can be included as [custom keys](#custom-keys) regardless of how they were processed here.

### license

`license`, see [4.7.1 License](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

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
remaining fields (`documentation` and `software` or only `software`) may be included as [custom keys](#custom-keys).

### licensor

`licensor`, see [4.7.2 Licensor](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

```
"name" = okh:licensor
```

### making instructions

`making-instructions`, see [4.8.7 Assembly Instructions](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

```
"path" = okh:manufacturingInstructions
```

### operating instructions

`operating-instructions`, see [4.8.12 Operating Instructions](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

```
"path" = okh:userManual
```

### software

`software`, see [4.8.15 software](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

```
create okh:software
"title" = label of okh:software
"path" = okh:release
```

### standards-used

`standards-used`, see [4.6.14 Standards used](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

```
if
    "reference" isnotempty
        "reference" = okh:standard
elseif
    "standard-title" isnotempty
        "standard-title" = okh:standard
```
The OKHv1 fields can be included as [custom keys](#custom-keys) regardless of how they were processed here.

###  Sub-Thing

`sub`, see [4.6.17 Sub-thing](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

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

The following data fields are either ignored or the same way included as custom keys.

- `contact`
- `contributors`
- `design-files`/ `schematics`/ `manufacturing-files`, see [4.8.3 ff. Design Files](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)
    - sadly their definition/use is too vague/messy to map them directly onto OKHv2, however these are still valuable fields
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
