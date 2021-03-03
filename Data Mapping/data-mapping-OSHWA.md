---
title: Ontology Mapping | OSHWA → OKHv2
---

# Notes

The Open Source Hardware Association created the [definition of Open Source Hardware](https://www.oshwa.org/definition) and launched [the first certification programme for OSH](https://certification.oshwa.org/).

Certified projects are listed here: <https://certification.oshwa.org/list.html>

Since OSHWA released an [API](https://certificationapi.oshwa.org/) making the metadata of certified projects available for the general public (plus you can apply for certification directly via this API).

Source for the mapping: token from [here](https://certificationapi.oshwa.org/) (see [issue 9](https://github.com/OPEN-NEXT/LOSH/issues/9#issuecomment-733939646) for details)

# Data fields

## direct matches

"responsibleParty": "Google, LLC",
"projectName": "Authboard",
"projectVersion": "1.0",
"projectDescription": "A board that goes in an Authbox to power a Raspberry Pi and handle the actuators for controlling access to tools based on membership or training.",   
"documentationUrl": "https://github.com/google/makerspace-auth/tree/master/hardware",
"hardwareLicense": "Other",

##  fields with rules

### category mapping

category mapping:
 "primaryType": "Electronics",
    "additionalType": [
      "Tool"
    ],

## Custom Data Fields

The following data fields are either ignored or the same way included as custom keys.

"country": "United States of America",
"publicContact": "thatch@google.com",
"projectWebsite": "https://github.com/google/makerspace-auth/",
"projectKeywords"
"softwareLicense": "Apache",
"documentationLicense": "Other",
"certificationDate": "2018-01-17T00:00-04:00"
"oshwaUid": "US000093",