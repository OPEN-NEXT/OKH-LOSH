LOSH Entity Relationships
===

``` mermaid
erDiagram
    TOSH ||--|{ MOSH : has
    MOSH ||--|{ source : has
    MOSH ||--|{ export : has
    MOSH ||--o{ POSH : has
    MOSH ||--o{ other-MOSH : has
    MOSH ||--o{ functionalMetadata : has
    MOSH ||--o{ productionMetadata : has
    POSH ||--o{ functionalMetadata : has
    POSH ||--o{ productionMetadata : has
    POSH ||--|{ source : has
    POSH ||--|{ export : has
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
    source {
        path source-file
    }
    export {
        path source-file
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