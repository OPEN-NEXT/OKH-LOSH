---
title: Ontology Mapping | OSHWA → OKH-LOSHv1
---

# Notes

The Open Source Hardware Association created the [definition of Open Source Hardware](https://www.oshwa.org/definition)
and launched [the first certification programme for OSH](https://certification.oshwa.org/).

Certified projects are listed here: <https://certification.oshwa.org/list.html>

Since OSHWA released an [API](https://certificationapi.oshwa.org/)
making the metadata of certified projects available for the general public
(plus you can apply for certification directly via this API).

Source for the mapping: token from [here](https://certificationapi.oshwa.org/)
(see [issue 9](https://github.com/OPEN-NEXT/LOSH/issues/9#issuecomment-733939646)
for details)

# Data fields

## direct matches

```
"projectName" = okh:name
"projectVersion" = okh:version
"projectDescription" = okh:function
"documentationUrl" = okh:repo
"responsibleParty" = okh:licensor
```

## fields with rules

### category mapping

At the moment we'll process `primaryType` only (with 3 exceptions).
See the following table how OSHWA categories are mapped onto the CPC system.

```
"unmappable-categories":[
        "Arts" ,
        "Education" ,
        "Environmental",
        "Manufacturing",
        "Other" ,
        "Science",
        "Tool"
        ]
if
    "primaryType" in "unmappable-categories"
            use first entry of "additionalType" instead
elseif
    no entry available other than "unmappable-categories"
        do nothing
else
    see table below
```

| OSHWA           | cpc:Classification |
|-----------------|--------------------|
| 3D Printing     | B33Y               |
| Agriculture     | A01                |
| Electronics     | H                  |
| Enclosure       | F16M               |
| Home Connection | H04W               |
| IOT             | H04                |
| Robotics        | B25J9/00           |
| Sound           | H04R               |
| Space           | B64G               |
| Wearables       | H                  |

### license

- get `hardwareLicense` only

```
if
    "hardwareLicense" = "other" → entry = `alternativeLicense`
else
    "hardwareLicense" = okh:spdxLicense
```

## Custom Data Fields

The following data fields are either ignored or the same way included as custom keys.

- `certificationDate`
- `country`
- `documentationLicense`
- `projectKeywords`
- `projectWebsite`
- `publicContact`
- `responsibleParty`
- `softwareLicense`
- `oshwaUid`
