https://ericrie.se/2015/08/07/cleaning-up-after-a-twitter-hack-with-unix/

My twitter account got hacked. I needed a way to bulk unfollow the 700 accounts I was now following. I installed the command line twitter client twidge and used a little shell-fu to unfollow the spam accounts in bulk.

```sh
twidge lsfollowing > following.txt
```

I edited this to remove the account I wanted to keep.

```sh
cat following.txt | xargs -L 1 twidge unfollow
```

Don't [UUOC](https://en.wikipedia.org/wiki/Cat_(Unix)#Useless_use_of_cat) me, I prefer left to right style for clarity.
