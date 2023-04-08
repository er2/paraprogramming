```sh
http  "https://en.wikipedia.org/wiki/International_Criminal_Court" | pup 'body > script:nth-child(4) text{}' | jq | sqlite-utils insert wiki.db articles -
```

Open wiki.db in IntelliJ. 

Generate CREATE TABLE script.

Create new supabase project.

Create table.

```sh
http  "https://en.wikipedia.org/wiki/International_Criminal_Court" |\
 pup 'body > script:nth-child(4) text{}' |\
 jq 'with_entries( .key |= ascii_downcase )' |\
 curl -X POST 'https://hebhfxipgvvjeqzwuptk.supabase.co/rest/v1/articles' \
 -H "apikey: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImhlYmhmeGlwZ3Z2amVxend1cHRrIiwicm9sZSI6ImFub24iLCJpYXQiOjE2NzkyNjUzMDAsImV4cCI6MTk5NDg0MTMwMH0.k3cFHsbX84Siw7ftpem3mhbP_yleuWai8z-16COjr6M" \
 -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImhlYmhmeGlwZ3Z2amVxend1cHRrIiwicm9sZSI6ImFub24iLCJpYXQiOjE2NzkyNjUzMDAsImV4cCI6MTk5NDg0MTMwMH0.k3cFHsbX84Siw7ftpem3mhbP_yleuWai8z-16COjr6M"       
 -H "Content-Type: application/json"       
 -H "Prefer: return=minimal"       
 -d @-
```

### snags
Supabase automatically lowercases column names, hence the line `jq 'with_entries( .key |= ascii_downcase )'`

```shell
http  "https://en.wikipedia.org/wiki/International_Criminal_Court" |\
 pup 'script[type="application/ld+json"] text{}'
```