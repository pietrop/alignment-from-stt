## Sample material
In the interest of making the sample material reproducible, decided to use two sample datas, the first chapter from the "Moby Dick" book by Herman Melville. and a Ted Talk.

The ted Talk seems to have a bit more errors in the STT that are slightly easier to spot and overall more representative of STT accuracy in the wild.

### Moby dick chapter 1

[LibriVox](https://librivox.org/moby-dick-by-herman-melville/) provides the audio book version and link to [project gutenberg](http://www.gutenberg.org/ebooks/2701) text version.

Direct links

- [Text](http://www.gutenberg.org/files/2701/2701-0.txt) - `12` kb
- [audio - Stewart Wills](http://ia802604.us.archive.org/32/items/moby_dick_librivox/mobydick_001_002_melville.mp3) - `21.9` MB
<!-- - alternative audio by [ Tilda Swinton](https://soundcloud.com/moby-dick-big-read) `20.7`MB as part of The Moby-Dick Big Read project -->

To bloating the github repository the audio file is not included in this repository. However the text for the first chapter can be found in [`/sample-data/moby-dick/moby-dick-chapter-1.txt`]( ./sample-data/moby-dick/moby-dick-chapter-1.txt).


The `sample-data` folder also contains the STT json for the first chapter of Moby Dick from LibriVox as transcribed by the BBC Kaldi system 
[`/sample-data/moby-dick/moby-dick-kaldi-stt.json`]( ./sample-data/moby-dick/moby-dick-kaldi-stt.json).

You could replace this with your own STT json from another service, provided you have access to an array of words, with `start`, `end`, and `text` attribute. These are needed by the aligner module to do the alignment.

### Ted Talk

Another one is a TED Talk by [Kate Darling: Why we have an emotional connection to robots ](https://www.ted.com/talks/kate_darling_why_we_have_an_emotional_connection_to_robots/transcript?language=en)
- [video](https://download.ted.com/talks/KateDarling_2018S-950k.mp4)
- [Transcript](https://www.ted.com/talks/kate_darling_why_we_have_an_emotional_connection_to_robots/transcript?language=en) copied from interactive web page and normalised.


data:
- accurate text transcription [`./sample-data/ted-talk-Kate-Darling-robot-emotions/ted-talk-transcript.txt`](./sample-data/ted-talk-Kate-Darling-robot-emotions/ted-talk-transcript.txt)
- transcript json from BBC Kaldi [`./sample-data/ted-talk-Kate-Darling-robot-emotions/ted-talk-bbc-kaldi.json`](./sample-data/ted-talk-Kate-Darling-robot-emotions/ted-talk-bbc-kaldi.json)
