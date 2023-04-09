```nu
open /usr/share/dict/words | from csv --noheaders | rename word | into sqlite words.db -t dict
open sentences.txt | split words | wrap word | into sqlite words.db -t corpus
sqlite3 words.db 'select word from corpus where lower(word) not in (select lower(word) from dict);'
```

```shell
aspell list < sentences.txt
```