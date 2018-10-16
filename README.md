I couldn't find something like this already.

There is probably a fancier way to do it with sed or awk or something, but
this got the job done for me.

It takes each line of input, and turns it into a proper grammatical list.

Examples, based on an infile made like this:

```bash
$ cat > infile
first thing
second thing
yet another thing
last thing
[ctrl+d]
```

By default, it formats properly:

```
$ cat infile | ./gramlist
first thing, second thing, yet another thing, and last thing
```

If you don't want 'and', just specify your conjunction as an argument.  If you
try to specify more than one, it takes the last one.

```
$ cat infile | ./gramlist or
first thing, second thing, yet another thing, or last thing
$ cat infile | ./gramlist what the heck
first thing, second thing, yet another thing, heck last thing
```

Use the -o flag to format improperly by [o]mitting the Oxford comma:

```
$ cat infile | ./gramlist -o
first thing, second thing, yet another thing and last thing
$ cat infile | ./gramlist -o or
first thing, second thing, yet another thing or last thing
```
