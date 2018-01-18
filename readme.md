# LevelDB in One Hour

[sourceranks-data](https://github.com/nice-registry/sourceranks/tree/master/packages/sourceranks-data)
is @zeke's first attempt to use LevelDB. This project led to some questions
for @juliangruber.

```sh
git clone https://github.com/nice-registry/sourceranks
cd packages/sourceranks-data
```

Questions to ask:

- Which module(s) should I install? (@level org needs some featured repos maybe)
- I see lots of callbacks in the docs. What's promisified and ready for async functions?
- How to save JSON? DIY Stringify?
- Timestamps?
- out of memory: https://gist.github.com/zeke/be521063146be0ec05049edb505e05c2
- streams
	- https://github.com/nice-registry/all-the-packages#why-streams
	- https://github.com/nice-registry/all-the-packages/blob/master/index.js
- search
- indexing? (no)
- emptying an entire database?
- level repl and/or CLI ?
	- https://www.npmjs.com/package/leveldb-repl
	- https://github.com/fitzgen/glob-to-regexp enables queries like 'get *sess*'
	- I can't get `lev` to work
- objects can be keys?! (Key design must be an art...)
- are keys case sensitive?
- can multiple keys reference the same object?
- how does leveldb work in the browser?
