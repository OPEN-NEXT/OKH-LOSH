<!--
SPDX-FileCopyrightText: 2021 Martin Häuer <martin.haeuer@ose-germany.de>
SPDX-FileCopyrightText: 2021 Robin Vobruba <hoijui.quaero@gmail.com>

SPDX-License-Identifier: GPL-3.0-or-later
-->

---
title: Ontology Mapping | appropedia.org → OKH-LOSHv1
---

# Notes

Appropedia properties are documented [on their Wiki](
https://www.appropedia.org/Template:Infobox_project).
The list of appropedia projects lies [on their Wiki too](
https://www.appropedia.org/w/index.php?title=Special:WhatLinksHere/Template:Infobox_project&limit=500).

We have [a script that scrapes the projects meta-data on the appropedia.org Wiki,
and converts it to manifest files](
https://github.com/OPEN-NEXT/LOSH-Appropedia-Scraper).
The details for how the mapping works,
can be found in the `apppropedia2okh` function in [the main script](
https://github.com/OPEN-NEXT/LOSH-Appropedia-Scraper/blob/main/scraper.py#L111).
