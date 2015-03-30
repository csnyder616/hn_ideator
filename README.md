# ![Logo: white lightbulb on HN orange](https://pbs.twimg.com/profile_images/581815557227327488/JMxj7rw3_normal.png) Show HN: hn_ideator
## A beautiful, highly opinionated project headline generator written in Ruby.

**[![Twitter logo](https://g.twimg.com/dev/documentation/image/Twitter_logo_blue_32.png) Follow the bot on Twitter](https://twitter.com/hn_ideator)**

Anyone who regularly visits [Hacker News](http://news.ycombinator.com) has seen the *"Show HN: {proper noun} — a[n] {adjective} {noun} written in {trendy language}”* headlines. Inspired by a [HN comment](https://news.ycombinator.com/item?id=9280555) surmising that all HN project descriptions are really written by Markov chains, I decided to write a Twitter bot that generates “Show HN”-style headlines.

### Approach
Since this bot generates headlines (rather than the longer project descriptions the original author described), I decided that a Madlib-style approach would be appropriate. It follows the following pattern:

> Show HN: {proper noun} — a[n] [{adverb}] {adjective} {noun}, [{adverb}] {verb} in {language}

#### {proper noun}
The goal here was to create a new “word” to describe the project:

1. Word length picked at random
1. Random characters are selected; the random character picker biases towards consonants or vowels based on the previous character
1. Capitalize the first letter, as well as other characters at random for CamelCasing
1. Occasionally add a trendy suffix like *.ly*, *Box*, etc.

#### {adverb}s, {adjective} and {noun}
Uses [WordNet](https://wordnet.princeton.edu/) to get random characters from the needed part of speech, using [indefinite_article](https://github.com/rossmeissl/indefinite_article) to add the article before the adverb or adjective

#### {verb}
Right now, it just picks from a pre-determined list. I tried to use WordNet to get synonyms (or words from the same domain as "written"), but I couldn't figure out how to get results that made any semblance of sense.

#### {language}
Picks a language at random from the included langs.txt. The languages were scraped (see the included prog_languages script) from the Wikipedia listings for [serious](http://en.wikipedia.org/wiki/List_of_programming_languages) and [esoteric](http://en.wikipedia.org/wiki/Esoteric_programming_language) programming languages.

### Twitter
When called with the "post" command-line argument, the generated headline will be posted to Twitter. This requires Twitter API access and user authorization.

## Copyright
Copyright 2015 [Chris Snyder](http://www.snyder616.com), released under the [MIT license](http://choosealicense.com/licenses/mit/).
