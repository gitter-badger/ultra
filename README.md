# Ultra
[![Build Status](https://travis-ci.org/venantius/ultra.svg?branch=master)](https://travis-ci.org/venantius/ultra)
[![Dependency Status](https://www.versioneye.com/user/projects/54b5674f050646ca5c000068/badge.svg?style=flat)](https://www.versioneye.com/user/projects/54b5674f050646ca5c000068)

Hey, you know who has two thumbs and strong opinions? That's right, it's me.

Ultra is a Leiningen plugin for an absolutely kick-ass development environment.

I've written a blog post describing Ultra in greater depth [here](http://blog.venanti.us/ultra).

## Installation

To install and configure Ultra, add something like the following to your `~/.lein/profiles.clj`

```clojure
{:user {:plugins [[venantius/ultra "0.3.3"]]
        :ultra {:color-scheme :solarized_dark}}}
```

### Requirements

Colorized nREPL output requires Leiningen version 2.4.2 or higher.

The plugin at large needs JDK 7+.

#### ClojureScript Support

At the moment, Ultra doesn't have ClojureScript support at the REPL. See https://github.com/brandonbloom/fipp/issues/7.

## Features
For a detailed list of features, check out the [wiki](https://github.com/venantius/ultra/wiki). Here's the highlight reel:

*A colorized REPL!*
![colorized repl](https://venantius.github.io/ultra/images/colorized-repl.png)

*[Clearer test output](https://github.com/venantius/ultra/wiki/Tests)!*
![test output demo](https://venantius.github.io/ultra/images/test-output.png)

*Better stacktraces!*
![test stacktrace demo](https://venantius.github.io/ultra/images/colorized-test-stacktrace.png)

*[Java object introspection](https://github.com/venantius/ultra/wiki/Java)!* 
![java introspection](https://venantius.github.io/ultra/images/java-interop.png)

## Configuration

All of the above features are enabled by default, but can be turned off by setting a `false` flag in your profile. If you wanted Ultra to essentially no-op, your profile would look like this: 

```clojure
{:user {:plugins [[venantius/ultra "0.3.3"]]
        :ultra {:repl         false
                :stacktraces  false
                :tests        false
                :java         false}}}
```

### Color schemes

At the moment Ultra supports the following color schemes:
 - `:solarized_dark`
 - `:default`

If you want to set the colors yourself instead of using a theme you can configure them directly, e.g.:

```clojure
{:user {:plugins [[venantius/ultra "0.3.3"]]
        :ultra {:color-scheme {:delimiter [:red]
                               :tag [:red]
                               :nil [:cyan]
                               :boolean [:cyan]
                               :number [:cyan]
                               :string [:cyan]
                               :character [:cyan]
                               :keyword [:green]
                               :symbol nil
                               :function-symbol [:blue]
                               :class-delimiter [:blue]
                               :class-name nil
                               :exception nil}}}}
```

## Contributing

Please open an issue here before submitting pull requests; I prefer to have documentation and consensus that either of our time will be well spent by working on it. When opening an issue -- particularly for bugs -- please refer to [CONTRIBUTING.md](https://github.com/venantius/ultra/blob/master/CONTRIBUTING.md)

Bug fixes and code cleanup are always appreciated and won't get too much pushback; new features will be held to a higher standard - this whole project is something of a massive exercise in ego, after all.

Pull Requests for new color schemes welcome; please include screenshots in your submission.

## Motivation

...or, why didn't you just put all of this stuff in your `~/.lein/profiles.clj`?

In short, my `:user` profile was starting to become bloated. It was difficult to tell whether plugins were interfering with each other, and my `:injections` key in particular was starting to look a little unwieldy. 

At some point I realized I was up to my neck in alligators and that it was time to push things into a standalone repository.

## Special Thanks

Ultra wraps, calls, or draws inspiration from the following libraries, and their owners and authors deserve credit for doing most of the hard work.  

 - [AvisoNovate/pretty](https://github.com/AvisoNovate/pretty) - Better exceptions
 - [brentonashworth/lein-difftest](https://github.com/brentonashworth/lein-difftest) - Lein-difftest - test diffs using difform
 - [greglook/puget](https://github.com/greglook/puget) - Colorized pretty-printing
 - [greglook/whidbey](https://github.com/greglook/whidbey) - Puget nREPL middleware
 - [jaycfields/expectations](https://github.com/jaycfields/expectations) - The Expectations testing library
 - [pjstadig/humane-test-output](https://github.com/pjstadig/humane-test-output) - Diffs in tests using clojure.test
 - [zcaudate/hara](https://github.com/zcaudate/hara) - General purpose clojure utility library
 - [zcaudate/vinyasa](https://github.com/zcaudate/vinyasa) - Give your Clojure workflow more flow

## License

In some cases, I've borrowed code snippets from libraries above and re-written them. Where that is the case, the Copyright of the original author[s] remains in effect. Any modifications to their code, as well as all original content, is Copyright © 2015 W. David Jarvis.

Distributed under the Eclipse Public License 1.0, the same as Clojure.
