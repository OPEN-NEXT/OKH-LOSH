### How to create an `okh.json` file for a project

#### `okhv`

`2.0`

#### `licensor`

`Firstname Lastname <Email>`

example: `licensor: Jane Doe - jane.doe@email.com`

#### `patent-class` (optional)

Search for your product type here
https://www.wipo.int/classifications/ipc/ipcpub/?notion=search
and click yourself through the options,
until you find the right IPC patent class.

example: `patent-class: G06C 7/02`

#### `spdx-license` (optional)

> NOTE:
> You only need to set this,
> if it can not be fetched from your repository hosters API.

Look for the *identifier* for your license in this list:
https://spdx.org/licenses/

example: `spdx-license: MIT` or `spdx-license: CC-BY-SA-4.0`

see also: [`license`](#license)

#### `license` (optional)

> NOTE:
> You only need to set this,
> if it can not be fetched from your repository hosters API,
> and if the license you use is not in the SPDX list.

Either put the whole license text verbatim,
or add a URL to the license-text.

example: `license: https://spdx.org/licenses/CC-BY-SA-4.0.html`

see also: [`spdx-license`](#spdx-license)

#### `image`

Enter a URL to an image showing off the OSH.
You may use more then one,
but please use at leat one,
and note that the first one is going to be the main one,
which will be used whenever only one of the images is to be shown.

example: `image: https://user-images.githubusercontent.com/736191/49698496-0c3c0c80-fc08-11e8-87bc-4fd2aa7f3f78.jpg`

#### `language` (optional)

Per default this will be `en_US`.

example: `language: jp_JP`

#### `function`

Think of this as a description of the OSH:
what it is used for,
how it works,
what its characteristics are that differentiate it from similar products,
...

example: 'function: The Corne is a 40% split mechanical USB general purpose keyboard. It is made up of two halves with 3x6 column staggered keys and 3 thumb keys. It has full RGB backlighting, and is fully programmable using the popular Open Source QMK firmware. The basic design principles are, to have a minimal, ergonomically arranged set of keys that are all reachable by moving a finger by at most a distance of one key in diagonal.
'

#### `sBoM` (optional)

URL to the simplified Bill of Materials.
By default, this will point to the URL of this meta-data file (`.okh.json`),
with just the file-name replaced with `sBoM.csv`.

example: `sBoM: https://raw.githubusercontent.com/ORG/PROJECT/BRANCH/sBoM.csv`

#### `source` (optional)
