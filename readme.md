![leveldb](https://user-images.githubusercontent.com/2289/35121759-6490fb0a-fc51-11e7-9dfd-dde9e2d09765.png)

LevelDB is a key-value store created by Google for use in the Chromium browser.
In typical Node.js style, some cool kids have run wild with the technology and
found many exciting new uses for it outside of the browser.

I sat down with LevelDB aficionado [Julian Gruber](http://juliangruber.com/)
to talk about what LevelDB is, how to use it, and where the project is headed.

As a GitHub employee, I have an annual budget that I can spend on 
"Learning and Development". In exchange for Julian's time I donated $100 to 
his charity of choice, 
[Code for Science & Society](https://donate.datproject.org/). 
Thanks to GitHub and Julian for making this possible. 🙏

## The Video

Here's the video of our 40-minute conversation:

📺 [Watch on YouTube](https://www.youtube.com/watch?v=-ofwZi9Xj44)

## Questions / Notes

#### I'm just getting started with LevelDB. Which module(s) should I install?

```sh
npm install level
```

[level](https://ghub.io) is the batteries-included module that most people should use. It bundles
[levelup](https://ghub.io/levelup) and
[leveldown](https://ghub.io/leveldown), 
and defaults to using the file system for storage.

#### Where are the good LevelDB modules?

The [@Level](https://github.com) org on GitHub has many, but there are more in 
npm userland. Most packages start with `level-`. GitHub search is handy for 
this.

#### Callbacks? Promises? Async/Await?

As of version 2, `level` supports Promises (and still support node-style 
callbacks too). If you omit the callback argument, you'll get a Promise. 
This means you can do this:

```js
const main = async () => {
  const db = level('./my-db')

  await db.put('foo', 'bar')
  console.log(await db.get('foo'))
}
```

As for the rest of LevelDB userland, many module still use callbacks. Your 
mileage may vary.

#### Native Modules

As of version 2, `level` uses [prebuild](https://github.com/prebuild/prebuild),
for native code compilation. This means when you install `level`, your machine
downloads a precompiled binary for your system from GitHub Releases, rather
than compiling it on the fly.

#### How to save JSON?

To save JSON objects, set the `valueEncoding` option when initializing the
DB:

```js
const db = level('./db' {valueEncoding: 'json'})
```

This will allows you to save JSON with `db.put()` and retrieve it with 
`db.get()`, without stringifying and parsing it yourself.

#### Timestamps

LevelDB doesn't have timestamps. Roll your own.

See also 
[level-ttl](https://ghub.io/level-ttl) and 
[level-version](https://ghub.io/level-version)

#### Search

We didn't get too much into this, but it sounds like the essential things
is key design. If space is not an issue, your keys can be very long.

See also [level-search](https://ghub.io/level-search)

#### CLI / REPL

Tools for interacting with your LevelDB:

- [leveldb-repl](https://ghub.io/leveldb-repl)
- [lev](https://ghub.io/lev)
- [ldb](https://github.com/0x00A/ldb)
