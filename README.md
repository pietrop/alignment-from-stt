# `alignment-from-stt`
<!-- _One liner + link to confluence page_

_Screenshot of UI - optional_ -->

Fork of [`BBC/alignment-from-stt`](https://github.com/bbc/alignment-from-stt)

> Work in progress, originally developed by Mathieu Triay, in BBC R&D as part of the New News prototype "fast forward". Being refactored into a reusable module by News Labs.

<!--
BBC Transcription Model  

- check/test Adapter Kaldi to Transcription model with alignement.json output. 
- autoEditJson Adapter to Transcription model?
- Transcription model to "adapter" autoEditJson. to do 2 ways
-->




## Setup

_stack - optional_

_How to build and run the code/app_

```
git clone git@github.com:pietrop/alignment-from-stt.git
```

```
cd alignment-from-stt
``` 

```
npm install 
```

## Usage


```
npm install alignment-from-stt
```

```js
const fs = require('fs');
const align = require('alignment-from-stt');
const automatedTranscription = require('../sample-data/kaldi-alignments.json').words;
// array of words, each .end, .start., .transcript_text;
const humanCorrectedTranscription = fs.readFileSync('./sample-data/human-transcription-on-one-line.txt').toString();

const reAlignedTranscription = align(humanCorrectedTranscription, automatedTranscription);

console.log(reAlignedTranscription)
```

See examples in `src/example-usage.js`.

Optional attributes

```js
var reAlignedTranscription = align(
  humanCorrectedTranscription,
  automatedTranscription,
  'word', // or punct, - optional textAttributeName
  true, // defaults to true - optional segmentationBasedOnSBD
  });
```

`textAttributeName` attribute for text field in word attribtue 
```js
{start: 0.2, end: 3, word: 'hello'} 
```
or 
```js
{start: 0.3, end: 6, punct: 'world'} 
```

by default  is set to `text`.

`segmentationBasedOnSBD` by default uses [`sbd`](https://www.npmjs.com/package/sbd) for sentence boundary detection. if set to false, then it spltis on `\n`. Helpful if you need more fine graine control on the lines you want to align. 



## System Architecture
<!-- _High level overview of system architecture_ -->

Input is 
- a json, array of words objects, with `start`, `end`, and `transcript_text`.
- plain text, humanan accurate, correct text.

Then `lib/text-segmentation` uses a sentence boundary detection module to split the human accurate plain text into an array of sentences. This avoid threating honorifics like `Mr.` as if they were sentence boundaries.

`lib/alignement` uses the segmented sentences and transposes the timecodes from the json (from STT) onto the accurate text. 

```js
...
  { start: 578.43,
    end: 582.52,
    text: '"The only thing I\'m here to discuss is your resignation," said Pashinyan.',
    words: [] },
  { start: 582.92,
    end: 594.12,
    text: 'Mr. Sargsyan walkedout, saying that Pashinyan had no right to speak on behalf of the people when his party had only received 7% of votes in the last elections.',
    words: [] },
  { start: 595.1,
    end: 600.86,
    text: 'Shortly afterwards, Nikol Pashinyan and other protest leaders were detained by the police.',
    words: [] },
...
```

At the moment it does so at sentence, level. Ideally will get to a point where it also reaches word level.


 

## Development env

 <!-- _How to run the development environment_

_Coding style convention ref optional, eg which linter to use_

_Linting, github pre-push hook - optional_ -->

- node > 8
- npm > 5.6.0


## Build

<!-- _How to run build_ -->

No build step for now
 

## Tests
<!-- _How to carry out tests_ -->
Unit tests written with jest.

```
npm run test
```

or 

```
npm run test:watch
```

If you want to run tests while developing - recommended.
 
See docs on [sample material](./docs/guides/sample-material.md)

## Deployment

<!-- _How to deploy the code/app into test/staging/production_ -->

publish to npm 
```
npm run publish:public
```

## TODO:

- [ ] there is an issue with this char `’` that is being escaped as `\\\'` in final result. it comes from .txt input file. should add check to replace as `'`.


<!-- ’ -->