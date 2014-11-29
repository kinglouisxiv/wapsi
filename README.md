# Wapsi #

Source files for an [Index](http://www.louisxiv.co.uk/wapsi/) to the [Wapsi Square](http://wapsisquare.com/) webcomic.

The index page is generated from two files: _index.txt_ and _tags.txt_. 

index.txt is the main list of comic pages and relevant tags -- characters and significant items. 

tags.txt has shortish explanation of the tags, where it is not glaring obvious from context. A tag does not need an entry in tags.txt.

Processing of the files through a python script [cig.py](https://github.com/kinglouisxiv/cig) allows simple markup through [Markdown](http://daringfireball.net/projects/markdown/syntax) and embedded html.

index.txt
---------

lines with leading ; are for comments, not processed.

Each page is described by a set of key:value pairs

Key	| Use
-----	|----
page:	| comic page ID, heads a comic page entry
date:	| date of page, preferably format consistent with other pages (YYYY-MM-DD suggested)
desc:	| a title or description of the page
note:	| other, non-story text, links 
tag:	| multiple tags for the page's story: one for each character, item, location, etc.
url:	| the actual comic page url - optional if baseurl: is set
baseurl | defines a common page url for succeeding pages. The page: ID is inserted for individual entries

**Suggestion**: page: and baseurl: should be left-aligned, other keys should have leading whitespace to clearly show their subordinate relationship to the preceding page: key.

desc: and note: are processed for Markdown formatting

example index page entry:

```
baseurl: http://wapsisquare.com/comic/{0}/
[...]
page:tired-of-hiding
	date: 2014-11-19
	desc: Tired Of Hiding
	note: An _example_ page entry
	tag: Bud
	tag: Kevin
	tag: LakeCalhoun
	tag: Snow
```

baseurl: http://wapsisquare.com/comic/{0}/ -- substitutes pageid: value for {0} giving a valid link

tags.txt
--------

The tags definition file is: 

- comments, marked by leading semicolon ";"
- tag & definition pairs, tab separated

**tag** as above: a tag value should be valid as an html class. Last definition wins.

**Processing**: definition text is processed for simple Markdown formatting & links, and html passthrough. Tags starting "ch-" are treated as chapter markers (not relevant to Wapsi perhaps?)

example tag entry: 

```
Amanda  	Amanda Erlich: photographer, [Monica's](#monica) childhood friend
```

