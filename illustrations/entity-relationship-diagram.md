<!--
SPDX-FileCopyrightText: 2021 Martin Häuer <martin.haeuer@ose-germany.de>
SPDX-FileCopyrightText: 2021 Robin Vobruba <hoijui.quaero@gmail.com>

SPDX-License-Identifier: GPL-3.0-or-later
-->

LOSH Entity Relationships
===

see a rendered version [here](https://pad2.opensourceecology.de/s/cheq933Dd)

``` mermaid
erDiagram
    TOSH ||--|{ MOSH : has
    MOSH ||--|{ sourceFile : has
    MOSH ||--|{ exportFile : has
    MOSH ||--o{ POSH : has
    MOSH ||--o{ other-MOSH : has
    MOSH ||--o{ functionalMetadata : has
    MOSH ||--o{ productionMetadata : has
    POSH ||--o{ functionalMetadata : has
    POSH ||--o{ productionMetadata : has
    POSH ||--|{ sourceFile : has
    POSH ||--|{ exportFile : has
    TOSH {
        URL repo
    }
    MOSH {
        structuredValue okhv
        URL snapshot-reference
        string name
        structuredValue version
        string spdx-license
        string licensor
        path image
        string documentation-language
        string open-technology-readiness-level
        string function
        string cpc-patent-class
        string tsdc-id
        path bom
    }
    POSH {
        path image
        string tsdc-id
    }
    sourceFile {
        string file-path
        string file-format
    }
    exportFile {
        string file-path
        string file-format
    }
    functionalMetadata {
        string free-keys
    }
    productionMetadata {
        string technology-specific-keys
    }
    other-MOSH {
    URL release-reference
    }

```
