# URL Poller
[![Build Status](https://travis-ci.org/Gelio/url-poller.svg?branch=master)](https://travis-ci.org/Gelio/url-poller)
[![Code Climate](https://codeclimate.com/github/Gelio/url-poller/badges/gpa.svg)](https://codeclimate.com/github/Gelio/url-poller)
[![Test Coverage](https://codeclimate.com/github/Gelio/url-poller/badges/coverage.svg)](https://codeclimate.com/github/Gelio/url-poller/coverage)
[![Issue Count](https://codeclimate.com/github/Gelio/url-poller/badges/issue_count.svg)](https://codeclimate.com/github/Gelio/url-poller)

A fully customizable url poller and notifier

# Features
* polls multiple urls
* customizable poll interval
* creates a diff between the previous and current version upon changes
* handles HTTP authentication and any other option from
  the [request](https://github.com/request/request) library
* emits changes and notifies using [RxJS](https://github.com/ReactiveX/RxJS)
  giving you lots of possibilities to fit your needs



# Installation
```
npm install multiple-url-poller
```




# Example
``` javascript
const Poller = require('multiple-url-poller').Poller;

let interval = 5 * 1000;  // time in ms
let urls = ['https://time.is/'];
let poller = new Poller({ interval, urls });
let diffs$ = poller.getDiffObservable();
let subscription = diffs$
  .map(diffs => diffs.filter(singleDiff => singleDiff.added || singleDiff.removed))
  .subscribe(diffs => console.log('New diff', diffs));

poller.start();
```
[See it running in your browser](https://runkit.com/5893290537f788001396a4a3/5893290537f788001396a4a4)



# Contributing
If you would like to suggest a feature or report a problem please use the *Issues* tab on GitHub.

All pull requests are welcome! Before creating one, make sure there are no problems by running
the following commands:
``` bash
npm run lint
npm test
```

Creating unit tests for new features in your pull requests would also be splendid, although it is
not required.



# Author
The author of this project is [Grzegorz Rozdzialik](https://github.com/Gelio).
