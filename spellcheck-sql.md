# Spellcheck

One of the main inspirations for paraprogramming was this old archival video from AT&T

<iframe width="560" height="315" src="https://www.youtube.com/embed/tc4ROCJYbm0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

It demonstrates an elegant unix pipeline that spell checks a document.

Looking at it critically though, there are some issues:
1. The commands it uses aren't standard commands available today. Once translated to real commands like `tr` and `comm` 
they lose some of their elegance
2. The algorithm used involves some thinking ahead and thinking like a computer scientist that I don't think we can
necessarily expect a lay programmer to be able to do.

The following nushell solution loses some elegance as it translates between plain text, nuon and SQL, but I think it's
actually somewhat more straightforward and pragmatic.

```nu
open /usr/share/dict/words | from csv --noheaders | rename word | into sqlite words.db -t dict
open sentences.txt | split words | wrap word | into sqlite words.db -t corpus
sqlite3 words.db 'select word from corpus where lower(word) not in (select lower(word) from dict);'
```

```shell
aspell list < sentences.txt
```