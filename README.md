# pbn-stream

[![Travis build status](https://travis-ci.org/richardschneider/pbn-stream.svg)](https://travis-ci.org/richardschneider/pbn-stream)
[![Coverage Status](https://coveralls.io/repos/github/richardschneider/pbn-stream/badge.svg?branch=master)](https://coveralls.io/github/richardschneider/pbn-stream?branch=master) 
 [![npm version](https://badge.fury.io/js/pbn-stream.svg)](https://badge.fury.io/js/pbn-stream) 
 
**pbn-stream** parses and transforms a [Portable Bridge Notation](http://www.tistis.nl/pbn/) stream into a series of javascript objects via the [node stream](https://nodejs.org/api/stream.html#stream_api_for_stream_consumers) design pattern.  Each PBN object contains a `type` and other properties that describes the PBN line(s).

## Features

* Directive - `% PBN 2.1`
* Tag - `[Event "somewhere"]`
* Inherited tag value - `[Event "#"]` or `[Event "##somewhere"]`
* Section data added to previous tag

## Getting started

Install the latest version with [npm](http://blog.npmjs.org/post/85484771375/how-to-install-npm)

    > npm install pbn-stream

## Usage

Include the package

    const pbn = require('pbn-stream')

Process a PBN file

    fs.createReadStream('foo.pbn')
        .pipe(pbn())
        .on('data', data => {
            console.log(JSON.stringify(data));
        })
        .on('error', err => {
            process.stderr.write(err.message);
            process.exit(1);
        });
        

# Command line

A command line interface (`pbn`) is also available. It transforms a PBN file or `stdin` into JSON.

To transform a file, try something like:

    > pbn foo.pbn
     
To use with `*nix` pipes

    > cat foo.pbn | pbn

# License
The [MIT license](LICENSE).

Copyright © 2016 Richard Schneider [(makaretu@gmail.com)](mailto:makaretu@gmail.com?subject=ISQ)