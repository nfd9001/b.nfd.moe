---
layout: post
title: Studying and Notetaking in Our Age of Loneliness
author: nfd
tags:
    - medium
    - weird
---
Every handful of years,
some new master organizational tool shakes up how
weird productivity nerds
micromanage their lives,
and they inject their own ideosyncracies into that process,
and those ideas in turn get rolled into the
Productivity Memeplex.
It's a beautiful process to someone who works in software;
it conjures mental images of hopping distros and
editor colorschemes.

So, by Someone's request, here's a high-level overview
of how I *technically* manage studying right *now.*
I'm not gonna talk too much about my organizational structure
(e.g. some people use Getting Things Done,
Zettelkasten,
bullet journalling,
...),
because I don't *really* have that kind of a formalized structure.
I'm just describing some neat tools.

# Some backstory
So I used to try to read all the books and documents
that I didn't have around in dead-tree format 
on [Calibre](https://calibre-ebook.com/)'s reader.
I'd use a tablet PC, or a 2-in-1.
This is fine, if you're alright with reading books
on a bright screen for however many hours straight.
And there's probably perfectly-fine ways to take notes
through that process, depending on what you want.
It wasn't a great fit.

When I went off to university,
most of the printers around were pay-to-play.
The printers they set up in the Linux CS department labs,
however, weren't.
(They still haven't cut off my credentials;
if I've ever surprised you by making the printer surge
to life at 3AM to say "hello," sorry not sorry.)
So when I had papers to read,
sometimes I'd just `ssh` in,
huck them at a printer,
and pick them up next time I was in the building.
Clipping those papers together and marking them up
with a pen turned out to be a pretty good way
to study math-heavy topics, for me.

Eventually, I set sights on getting some sort of
e-ink device for reading books and other
longer-form content.
A neighbor's old Kindle Paperwhite served that purpose quite well for a while.
It was also *terrible* for larger PDFs and most technical docs.
So I set my eyes on trying to find a *large* e-ink device
capable of even loading some of the occasional monsters I needed.
I'd have a hard time writing an unqualified recommendation of the thing,
but as of the time of writing,
the best hunk of hardware for the job's
[reMarkable 2](https://remarkable.com/store/remarkable-2).

# The tablet
reMarkable 2's pretty good. Good piece of hardware. 
Somewhat too commercial for my tastes,
honestly, but until the [PineNote](https://www.pine64.org/pinenote/) is "a thing,"
it's easily the tool for the job,
assuming you have some technical chops.
(If you *don't* want to mess around with third-party modifications,
this isn't the document to read if you're trying to figure out if rM
is worth the price. Check their official ad copy;
the thing does what it says on the tin.
But feel free to read on, I won't get too crazy here.)

Third-party modifications of reMarkable are unsupported,
and pretty much anything custom that I'm mentioning here
*could* eventually leave you with the world evaporating under you.
This said, I'm not under the impression that reMarkable's team is particularly
likely to deliberately try to break your mods,

### Toltec
[This is your quick-and-easy entry to the rM modding community](https://toltec-dev.org/).
Grab a launcher, KOReader, and probably yaft.
*And back up your ssh password, and set up keypair logins.*
(And whatever else you want, there's a lot of fun hacks there.)


### Documents
The *hardware* is fine for basically anything,
so long as your copy's DRM free: none of the reader apps support DRM. 
`xochitl` is the program you're using when you first power a reMarkable on.
At the time of writing, xochitl only supports ePub and PDF.
Behind the scenes, upon opening an ePub, the tablet generates a PDF
with your preferred typographical settings.
This generated document *doesn't* at the time of writing support internal links,
footnotes, reference pages, or some similar niceties.
(Links in uploaded PDFs work about the way you'd expect.)
KOReader supports all of those things quite nicely, but *not* xochitl-style
document annotation with a pen.

Annotations are stored separately from these PDFs,
in an original but well-understood format.
Several third-party tools can merge and render these formats into one PDF,
as can the official software.
If you make notebooks,
you're basically making new PDFs on the spot to annotate.
With the subscription service,
you can run handwriting recognition on your notes, and send that text over email.
(The recognition's pretty good on my handwriting, and doesn't require a huge amount of cleanup.)

### rM Cloud
With an obnoxious subscription service, which I appear to be grandfathered into (hope it lasts?),
you can store documents to be copied to/from your device.
I use it quite a bit to automate moving data around from place to place.
Let's start with my script to copy documents and webpages to the thing.
rM offers an offical Chrome extension to do this;
if that works for you, great.
I usually use Firefox, so I had to make my own.
This depends on [rmapi](https://github.com/juruen/rmapi), 
[pandoc](https://pandoc.org/),
and wget.

```bash
#!/bin/bash
name=$(basename "$1")
ext="${name##*.}"
mkdir -p /tmp/link-to-rm
cd /tmp/link-to-rm || exit
if [ "$ext" = "pdf" ] || [ "$ext" = "epub" ]
then
    wget "$1"
else
    pandoc "$1" -o "$name.epub"
fi
rmapi mput /link-to-rm

if [ -n "$2" ]
then
    mkdir -p ~/link-to-rm-docs/
    cp ./* ~/link-to-rm-docs
fi
rm /tmp/link-to-rm/*
```
If your browser supports sending that URL off to another program
(e.g. [qutebrowser](...)),
you probably already know what to do.
Otherwise, you may need an extension like
[this one](https://addons.mozilla.org/en-US/firefox/addon/external-application/).
Now I click a button, or click on a context option after right-clicking a link,
and I can read the document on my tablet a few seconds later.
Very dumb, very hacky, does exactly what I need it to do,
and I use it several times a day.

I'll share another handy script I threw together in a bit.

# Obsidian
So, I've read a whole bunch of stuff.
I've taken a whole bunch of unstructured or weakly-structured notes,
some on my tablet,
and lots in a dead-tree notebook that I used back when I was still
mostly reading on my itty-bitty Kindle.
I wanted to find a way to move those unstructured/weakly-structured notes
into some sort of more-structured, searchable, linked knowledge base.
[Obsidian](https://obsidian.md/) is an obnoxiously elegant approach to this,
and supports all sorts of weird idiomatic notetaking styles very well.

In brief, Obsidian lets you make very lightweight personal wikis
out of [Markdown](https://en.wikipedia.org/wiki/Markdown) files.
(I'm super comfortable composing loads of text in Markdown!
[I'm doing it right now!](https://github.com/nfd9001/b.nfd.moe/tree/main/posts)
Obsidian even has a sort-of-passable vim mode built in!)

### Import rM document highlights to Obsidian
Since Markdown is so simple, it's not so hard to take structured data
and generate a structured Markdown document.
So a handful of minutes after I started messing with Obsidian,
inspiration struck!

[remarking](https://github.com/sabidib/remarking) is a little tool that
pulls documents off the reMarkable cloud,
collects the passages that you've highlighted in those documents,
and spits them out in various structured formats.
It's a great little utility that's super easy to glue to Obsidian.
Here's how I did it:

```py3
#! /bin/python3
import json
from datetime import datetime
import sys
import subprocess
import os

def readJson(s):
    j = json.loads(s)
    return (j["documents"], j["highlights"])

def getHighlightDictsForDoc(docdict, highlightdictlist):
    return [i for i in highlightdictlist if i["document_id"] == docdict["id"]]

def highlightsForDoc(docdict, highlightdictlist):
    l = ["# Highlights for " + docdict["name"]]
    hls = getHighlightDictsForDoc(docdict, highlightdictlist)
    for hl in hls:
        l.append("- On page " + str(hl["page_number"]))
        l.append("    - " + hl["text"])
        l.append("")
    return l

def generateSeveralLists(docs, highlights, rmtag):
    ls = []
    frontmatter  = ["---", "generated: " + str(datetime.now()), "rmtag: " + rmtag,
        "tags: highlight", "","---"]
    for doc in docs:
        l = []
        l = l + frontmatter
        l = l + (highlightsForDoc(doc, highlights))
        ls.append(("highlights-" + doc["name"] + ".md", "\n".join(l)))
    return ls

def main():
    if len(sys.argv) != 3:
        print("Usage: gen-md-remarkable-highlights.py (search tag) (save dir)")
    rmtag = sys.argv[1]
    savedir = sys.argv[2]
    print(rmtag)
    print(savedir)
    print("Getting results from remarking... (this may take a bit)")
    result = subprocess.run(
            ['remarking', 'run', 'json', rmtag],
            stdout=subprocess.PIPE)
    outputrawjson = result.stdout.decode('utf-8')
    o = readJson(outputrawjson)
    documents = o[0]
    highlights = o[1]
    lists = generateSeveralLists(documents, highlights, rmtag)

    try:
        os.makedirs(savedir)
    except FileExistsError:
        pass

    print("Writing files...")
    for item in lists:
        filename = item[0]
        data = item[1]
        print("    - Writing to " + savedir + "/" + filename)
        f = open(savedir + "/" + filename, "w")
        f.write(data)
        f.close()
    print("Done.")

if __name__ == '__main__':
    sys.exit(main())
```
...and now I can run this script and point it directly into 
my Obsidian dir.
(I use search tag-specific subdirectories.)

### dataview
Obsidian has a whole bunch of neat extensions.
[obsidian-dataview](https://github.com/blacksmithgu/obsidian-dataview/)
is *really* neat.
It lets you treat your notes as structured data,
and query them with a SQL-like DSL (or Javascript, if need be).
Here's some snippets I use in my main hub page, adapted from comment #5 [here](https://forum.obsidian.md/t/dataview-plugin-snippet-showcase/13673):

````
## Recently edited
```dataview
TABLE file.mtime as Edited
FROM !#highlight
WHERE date(now) - file.mtime <= dur(3 days) and file.name != "Index.md"
SORT file.mtime desc
LIMIT 5
```

## Recently created
```dataview
TABLE file.ctime as Created
FROM !#highlight
WHERE date(now) - file.ctime <= dur(3 days)
SORT file.ctime desc
LIMIT 5
```

## Loose
```dataview
LIST FROM !#highlight WHERE length(file.inlinks) = 0 AND length(file.outlinks) = 0

```
````

...which keeps the large number of semistructured highlights
from polluting my highly structured manual notes.
(I use very similar code for my highlight hub, just with ``#highlight``
instead of ``!#highlight``).

# So yeah
I hope some of this is useful!
