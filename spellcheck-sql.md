```nu
cat /usr/share/dict/words | from csv | into sqlite words.db -t dict
cat sentences.txt | split words | to text | sqlite-utils insert --csv words.db corpus - 
sqlite3 words.db 'select * from corpus where corpus.line not in (select A from dict);'
```

## TODO fix into sqlite treating first line as a header