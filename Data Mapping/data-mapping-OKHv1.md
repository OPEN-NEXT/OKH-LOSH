# From OKHv1 to OKHv2

The Open Know-How Manifest Specification Version 1.0
([OKHv1](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1))
gave a first approach to organise open source hardware via representative metadata.

## Notes

Source: [OKHv1 Section 4.5 ff](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

## Data fields

### direct matches

```
"title" = okh:name
"version" = okh:version
"image" = okh:image
"documentation-home" = okh:repo
"documentation_language" = okh:documentationLanguage
"bom" = okh:bom
```

###  fields with rules

#### date

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

####  sub-MOSH

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
    extract repo URL from "manifest"
```

#### description

`description`/`indended-use`/`health-safety-notice`

```
okh:function = "description" + "intended-use" + "health-safety-notice"
```

#### license

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

#### licensor

`licensor`, see [4.7.2 Licensor](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

```
"name" = okh:licensor
```

#### development-stage

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

#### standards-used

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

#### software

`software`, see [4.8.15 software](https://app.standardsrepo.com/MakerNetAlliance/OpenKnowHow/src/branch/master/1#d1e6bbfa-c5a8-4570-aba1-051898e1acf6)

```
create okh:software
"title" = label of okh:software
"path" = okh:release
```

## Custom Keys

The following data fields are either ignored or the same way included as custom keys.

- `contact`
- `contributors`
- `development-stage`/`made`/`made-independently` (see [field rules](#development-stage))
- `documentation-is-translation`
- `keywords`
- `license` (see [field rules](#license))
    - (`documentation`)
    - `sofware`
- `manifest-author`
- `manifest-is-translation`
- `manifest_language`
- `project-link`
- `standards-used` (see [field rules](#standards-used))



|   | OKHv1                        | OKHv2                            | Comment                                                                                                                                                                                      |
|---|------------------------------|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| x | date-created                 | timestamp                        |                                                                                                                                                                                              |
| x | date-updated                 | timestamp                        |                                                                                                                                                                                              |
| x | manifest-author              | -                                |                                                                                                                                                                                              |
| x | title                        | name                             |                                                                                                                                                                                              |
| x | description                  | function                         |                                                                                                                                                                                              |
| x | indended-use                 | function                         |                                                                                                                                                                                              |
| x | keywords                     | -                                |                                                                                                                                                                                              |
| x | Project Homepage             | -                                |                                                                                                                                                                                              |
| x | health-safety-notice         | function                         |                                                                                                                                                                                              |
| x | contact                      | -                                |                                                                                                                                                                                              |
| x | contributors                 | -                                | the wikibase instance may include contributor data, but not from manually created manifest files                                                                                             |
| x | image                        | image                            |                                                                                                                                                                                              |
| x | version                      | version                          |                                                                                                                                                                                              |
| x | development-stage            | development-stage                |                                                                                                                                                                                              |
| x | made                         | development-stage                | if(true) → `development-stage`='prototpye'; else → `development-stage`='in development'                                                                                                      |
| x | made-independently           | development-stage                | if(true) → `development-stage`='prototpye'; else → `development-stage`='in development'                                                                                                      |
| x | standards-used               | standard                         | only `standard-title` is copied into this field                                                                                                                                              |
| x | standards-used               | development-stage                | if(`certification` not empty) → `development-stage` = 'certified' (has priority); else → Null                                                                                                |
|   | derivative-of                | forkOf                           |                                                                                                                                                                                              |
|   | variant-of                   | forkOf                           |                                                                                                                                                                                              |
| x | sub                          | -                                |                                                                                                                                                                                              |
| x | License                      | spdxLicense / alternativeLicense | only the `hardware` is considered (even though `documentation would be correct`); if the field contains an SPDX License Identifier, `spdxLicense` is filled,  `alternativeLicense` otherwise |
| x | licensor                     | -                                |                                                                                                                                                                                              |
| x | documentation-home           | repository                       |                                                                                                                                                                                              |
|   | archive-download             | -                                |                                                                                                                                                                                              |
|   | design-files                 | -                                | included as `source` or `export`                                                                                                                                                             |
|   | schematics                   | -                                | included as `source` or `export`                                                                                                                                                             |
| x | bom                          | -                                | included as sBoM                                                                                                                                                                             |
|   | tool-list                    | -                                | included as `source` or `export`                                                                                                                                                             |
|   | making-instructions          | -                                | included as `source` or `export`                                                                                                                                                             |
|   | manufacturing-files          | -                                | included as `source` or `export`                                                                                                                                                             |
|   | risk-assessment              | -                                | included as `source` or `export`                                                                                                                                                             |
|   | tool-settings                | -                                | included as `source` or `export`                                                                                                                                                             |
|   | quality-instructions         | -                                | included as `source` or `export`                                                                                                                                                             |
|   | operating-instructions       | -                                | included as `source` or `export`                                                                                                                                                             |
|   | maintenance-instructions     | -                                | included as `source` or `export`                                                                                                                                                             |
|   | disposal-instructions        | -                                | included as `source` or `export`                                                                                                                                                             |
| x | software                     | -                                |                                                                                                                                                                                              |
| x | manifest_language            | -                                |                                                                                                                                                                                              |
| x | documentation_language       | -                                |                                                                                                                                                                                              |
| x | manifest-is-translation      | -                                |                                                                                                                                                                                              |
| x | documentation-is-translation | -                                |                                                                                                                                                                                              |

