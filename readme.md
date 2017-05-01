score-watcher
==============

[![Greenkeeper badge](https://badges.greenkeeper.io/bracketclub/score-watcher.svg)](https://greenkeeper.io/)
[![Build Status](https://travis-ci.org/bracketclub/score-watcher.png?branch=master)](https://travis-ci.org/bracketclub/score-watcher)

Score watcher for [bracket.club](https://bracket.club).

## Usage

```js
const ScoreWatcher = require('score-watcher');

new ScoreWatcher({
    // Required
    sport: 'ncaam',
    year: '2015',
    // An optional bracket to initialize the updater with
    // Will default to an empty bracket for the sport/year
    master: '',
    // Optional log file
    logger: null,
    // The callbacks
    onSave: function (master, cb) {
        // Will be called with each master as a string
        // `cb` is optional but should be used to ensure
        // that each bracket is saved before moving to
        // the next one
    },
    scores: {
        // Config for scores module
        interval: '1m',
        url: 'http://url.com'
    }
}).start();

```

## What is it doing?

It is setting up an async.queue and creating a watcher/emitter with [`scores`](http://github.com/bracketclub/scores). Then every time the queue drains, it calls `onSave` with the latest master (and an optional callback to notify the watcher when it has been added).

## Is it on npm?

Yeah, now that there are publically scoped modules it's at `npm install @lukekarrys/score-watcher`.

### LICENSE

MIT
