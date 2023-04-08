```nushell
http get "https://ericrie.se/feed/json" | from json | get items | into sqlite rss.db
sqlitebrowser rss.db
```

## TODO: merge duplicates on subsequent fetches