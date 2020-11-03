# Chasperli-box

Forked from [https://github.com/aceakash/project-name-generator](https://github.com/aceakash/project-name-generator).

Generate quirky swiss german expressions like *verrockts-Rüebli*, *sauglatts-Büsi*, *gäbigs-Gigampfi-2921* to use wherever you need a random but memorable name.

Useful for object names, temp folders, passwords, project names, unique ids etc

## Install
`npm install project-name-generator --save`

## Quick Start
```javascript
var generate = require('project-name-generator');

generate().dashed; // 'verrockts-Rüebli'

generate().spaced; // 'verrockts Rüebli'

generate().raw; // ['verrockts', 'Rüebli']

generate({ number: true }).dashed; // 'verrockts-Rüebli-7794'

generate({ words: 4 }).raw; // ['verrockts', 'abgspaceds', 'wüeschts', 'Rüebli']

generate({ words: 4, number: true }).dashed; // 'verrockts-abgspaceds-wüeschts-Rüebli-4298'

generate({ words: 2, alliterative: true }).spaced; // 'gäbigs Gigampfi'

```

## Quickstart CLI
This package contains a cli script.  You can pull in the package globally using npm
`npm install -g project-name-generator`

Call from your command line
```
$ project-name-generator
{ raw: [ 'verrockts', 'Rüebli' ],
  dashed: 'verrockts-Rüebli',
  spaced: 'verrockts Rüebli' }
```

For CLI options 
```
project-name-generator -h

Usage: project-name-generator [options]


Options:

  -V, --version          output the version number
  -w, --words [num]      number of words [2]
  -n, --numbers          use numbers
  -a, --alliterative     use alliterative
  -o, --output [output]  output type [raw|dashed|spaced]
  -h, --help             output usage information
```

## API
The module returns a single function, `generate(options)`

Calling `generate()` with no arguments will return an object:
```javascript
{
    raw: ['whispering', 'valley'],
    dashed: 'whispering-valley',
    spaced: 'whispering valley'
}
```

The `options` argument object can have properties

* **words** (number) - Number of words generated (excluding number). All words will be adjectives, except the last one which will be a noun. Defaults to **2**.
* **number** (boolean) - Whether a numeric suffix is generated or not. The number is between 1 - 9999, both inclusive. Defaults to **false**.
* **alliterative** (boolean) - Whether to output words beginning with the same letter or not. Defaults to **false**.

`generate({ words: 3 })` will return:
```javascript
{
    raw: ['harmonious', 'endurable', 'substance'],
    dashed: 'harmonious-endurable-substance',
    spaced: 'harmonious endurable substance'
}
```

`generate({ words: 5, number: true })` will return:
```javascript
{
  raw: [ 'exciting', 'cooperative', 'legal', 'lackadaisical', 'blood', 4099 ],
  dashed: 'exciting-cooperative-legal-lackadaisical-blood-4099',
  spaced: 'exciting cooperative legal lackadaisical blood 4099'
}
```

`generate({ words: 2, number: false, alliterative: true })` will return:
```javascript
{
  raw: [ 'elegant', 'experience' ],
  dashed: 'elegant-experience',
  spaced: 'elegant experience'
}
```

## Tests
To run tests locally:
```
npm install

npm test
```

The library has been tested with Node.js 12.18.4

## Todo

- Adjust form of adjective to the noun
