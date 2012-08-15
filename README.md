#nodefetch

One day I got fed up of going online to pull down the latest library I wanted, whether that be Backbone, jQuery, Underscore or a CSS library like Normalize.css. Of course great solutions like [JamJS](http://jamjs.org) exist for full blown package management but often I wanted something a bit easier, so I decided to test my Node skills and create a command line tool to do just that. The result is nodefetch. Essentially it's a wrapper around wget that allows you to save libraries you use often for easy access.

## Requirements

You need to have Node JS and NPM installed.

nodefetch also depends on the command line utility wget. If you're on a Mac and use homebrew, you can install with `brew install wget`.

At this time nodefetch has only been tested on Mac OS X Lion. If you run any other OS, please let me know if nodefetch works or not.

## Installation


```
npm install -g nodefetch
```

(If you get a permission error, you will need to try again as `sudo`):

```
sudo npm install -g nodefetch
```

You will then have the `nodefetch` executable ready for use.

## Usage

The first time you run nodefetch it will pull down a sample JSON file, `nodefetch.json` into your home directory. This file contains libraries and acts also as an example of how to add your own to nodefetch. It looks like so:

```json
{
  "backbone" : "http://backbonejs.org/backbone-min.js",
  "underscore" : "http://underscorejs.org/underscore-min.js",
  "jquery": "http://code.jquery.com/jquery.min.js",
  "json2": "https://github.com/douglascrockford/JSON-js/raw/master/json2.js",
  "normalize": "https://raw.github.com/necolas/normalize.css/master/normalize.css",
  "raphael": "http://github.com/DmitryBaranovskiy/raphael/raw/master/raphael-min.js",
  "reset": "http://meyerweb.com/eric/tools/css/reset/reset.css"
}
```

Here you can see how it works, it's a simple JSON file of key->value, with the key being how you reference the library through nodefetch, and the value being the URL to download. You can add to this as you please.

Once that's done, downloading jQuery is as simple as:

```
nodefetch jquery
```

__NEW__ you can pass in multiple libraries to download them all at once:

```
nodefetch jquery underscore backbone
```

If you want to specify the file name for the library, pass it in like so:

```
nodefetch jquery:jquery.js backbone underscore:u.js
```

That will download jQuery into `jquery.js`, download Backbone to a file named the same as the file on the server, and Underscore to `u.js`.

## Todo

This is my first NPM module so I'm still learning, but the most pressing TODOs are:

* Move `nodefetch.json` into the package for nodefetch so I can simply update the default one through Github.
* Improve error handling
* Rewrite to use [CommanderJS](https://github.com/visionmedia/commander.js) for better CLI.

## Contributing

The WIP branch is the __develop__ branch, so any contributors should:

* Fork the repository
* work on the __develop__ branch
* when you're ready to make a pull request, merge master INTO your develop branch
* make the pull request to merge your develop branch into master


## Testing

The tests are within the `test/` folder. To run them, simply run: `node tests` from within the test folder, or `node test/tests` from the project root.

Any questions, feel free to ask :)


## Changelog

#####V0.1.0
Big enough changes to warrant the step up to 0.1.0

* unit tests! (see above for how to use)
* rewrote to __no longer use wget__ but instead use [Request](https://github.com/mikeal/request/) which is on NPM. No more external dependencies ftw! Thanks @mheap for the recommendation
* large rewrite to support the above and unit tests. Code is a bit tidier now.
* the `nodefetch` object is now exported as a module.

#####V0.0.4
* able to download multiple libraries at once, new syntax for specifying the specific file name to download to (see above documentation)

#####V0.0.3
* inline help added through `nodefetch --help`
* colourised terminal output

#####V0.0.2
* Huge rewrite of the code to make everything easier

#####V0.0.1
* Initial Release

