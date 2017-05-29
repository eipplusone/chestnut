# chestnut

[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/plexus/chestnut?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Clojureverse](https://rawgit.com/clojureverse/clojureverse-assets/master/clojureverse-org-green.svg)](http://clojureverse.org/c/chestnut)

[![Clojars Project](http://clojars.org/chestnut/lein-template/latest-version.svg)](http://clojars.org/chestnut/lein-template)

<img align="left" alt="Mr. Chestnut" src="resources/chestnut.png">


**Getting value out of Chestnut? Consider making [a small donation](https://patreon.com/plexus).**

Chestnut is a Leiningen template for a Clojure/ClojureScript app based
on Om, Reagent, or Rum, featuring a great dev setup, and easy deployment.

For smooth development you get instant reloading of Clojure,
ClojureScript, and CSS. A browser-connected REPL is also included.

For deployment you get uberjar support, meaning you can get all your
code compiled, optimized, and packaged in a single executable JAR
file. It also contains the necessary artifacts to work on Heroku out
of the box.

**Need help?** Ask [on the mailing list](http://clojureverse.org/c/chestnut)
(issues on GitHub are for bugs. Feature requests can be done either on the
mailing list or on Github.)

This README may describe unreleased features. Please compare the
[version number on Clojars](https://clojars.org/chestnut/lein-template) to the
[changelog below](https://github.com/plexus/chestnut/blob/master/README.md#changelog),
and check the README in your generated project for instructions pertaining to
your version.

## Documentation

[Go to the documentation](http://plexus.github.io/chestnut/)

## Usage

**This README may describe unreleased features, instead you can check the [README for the latest stable release](https://github.com/plexus/chestnut/tree/v0.15.1/README.md)**

```
lein new chestnut <name> <options>

e.g.

lein new chestnut my-app +garden +reagent +http-kit
```

If you're using the snapshot version, then make sure to add a `--` to separate Leiningen's and Chestnut's arguments

```
lein new chesnut my-app --snapshot -- +garden +reagent +http-kit
```

After that open the README of your generated project for detailed
instructions, or consult the [Documentation](http://plexus.github.io/chestnut/)

### Lighttable

Lighttable provides a tighter integration for live coding with an inline
browser-tab. Rather than evaluating cljs on the command line with weasel repl,
evaluate code and preview pages inside Lighttable.

Steps: After running `(run)`, open a browser tab in Lighttable. Open a cljs file
from within a project, go to the end of an s-expression and hit Cmd-ENT.
Lighttable will ask you which client to connect. Click 'Connect a client' and
select 'Browser'. Browse to [http://localhost:3449](http://localhost:3449)

View LT's console to see a Chrome js console.

Hereafter, you can save a file and see changes or evaluate cljs code (without
saving a file). Note that running a weasel server is not required to evaluate
code in Lighttable.

### Emacs/Cider

Start a repl in the context of your project with `M-x cider-jack-in`.

Switch to repl-buffer with `C-c C-z` and start web and figwheel servers with
`(run)`, and weasel server with `(browser-repl`). Load
[http://localhost:3449](http://localhost:3449) on an external browser, which
connects to weasel, and start evaluating cljs inside Cider.

## List of Contents

This template gives you everything you need to start developing
Clojure/ClojureScript apps effectively. It comes with

* [Figwheel](https://github.com/bhauman/lein-figwheel) Automatically
  reload your ClojureScript and CSS as soon as you save the file, no
  need for browser refresh.
* [Om](https://github.com/swannodette/om) ClojureScript interface to Facebook's
  React. Alternatively you can use Reagent (`+reagent`), use Rum (`+rum`), or use `+vanilla` to
  do without a React wrapper.
* [Om-Next](https://github.com/swannodette/om) Next version of the ClojureScript interface to Facebook's React. Specify (`+om-next`).
* [Ring](https://github.com/ring-clojure/ring) Clojure's de facto HTTP
  interface. Chestnut uses a Jetty or HttpKit server to serve the
  Clojurescript app. This way you already have an HTTP server running
  in case you want to add server-side functionality. Chestnut also
  inserts a Ring middleware to reload server-side Clojure files.
* Heroku support. Chestnut apps have all the bits and pieces to be
  deployable to Heroku. Getting your app on the web is as simple as
  `git push`.
* Unit tests for both Clojure and CLJS.
  Both specs and CLJS tests can be run in "auto" mode.

## Options

General options:

- `+no-poll` Opt out of usage statistics poll
- `+http-kit` Use [HTTP Kit](http://http-kit.org/server.html) instead of Jetty
- `+site-middleware` Use the `ring.middleware.defaults.site-defaults` middleware (session, CSRF), instead of `ring.middleware.defaults.api-defaults` (see
  [ring.defaults documentation](https://github.com/ring-clojure/ring-defaults))
- `+code-of-conduct` / `+coc` Add the [contributor covenant](http://contributor-covenant.org/) Code of Conduct

Choice of UI library:

- `+vanilla` Don't include Om, use this if you intend to use some other view library
- `+om-next` Use om.next, instead of legacy Om
- `+reagent` Use Reagent instead of Om
- `+re-frame` Use Reagent and re-frame
- `+rum` Use Rum instead of Om

Choice of CSS style:

- `+less` Use [less](https://github.com/montoux/lein-less) for compiling Less CSS files.
- `+sass` Use SASS for generating CSS
- `+garden` Use Garden for generating CSS

## Local copy

If you want to customize Chestnut, or try unreleased features, you can
run directly from master like this:

``` sh
git clone https://github.com/plexus/chestnut.git
cd chestnut
lein install
```

Note that master may be partially or wholly broken. I try to do
extensive manual testing before releasing a new stable version, so if
you don't like surprises then stick to the version on Clojars. Issue
reports and pull requests are very welcome.

## Requirements

* Java 1.7 or later
* Leiningen 2

## FAQ

* **Q:** How can I get the features in the SNAPSHOT version? <br>
  **A:** Use leiningen's `--snapshot` flag, e.g. `lein new chestnut
         my-project --snapshot`
* **Q:** I'm seeing warnings while compiling ClojureScript. <br>
  **A:** There are a few known warnings, but they should not affect the
         functioning of your app.
* **Q:** I changed the `{:text "Hello Chestnut!"}` portion and saved
         the file, but the changes don't show up. <br>
  **A:** It's a feature. The `app-state` is defined with `defonce`, so your
         application state doesn't reset every time you save a file. If you do
         want to reset after every change, change `(defonce app-state ..)` to
         `(def app-state ...)`.
* **Q:** I just want to compile ClojureScript to fully optimized JavaScript, so
         I can use it in a static HTML site. <br>
  **A:** Compile the "min" ClojureScript build, like this: `lein cljsbuild once min`, then look
         for `resources/public/js/app.js`.
* **Q:** I gave my project a very generic name like `cljs` or `clojure` and now
         it's not working. <br>
  **A:** This is due to namespace clashes. Try picking
         a more unique name. In particular avoid namespace prefixes used by
         Clojure, Clojurescript, or existing libraries.

## Sources

I used the
[browser-connected-repl](https://github.com/cemerick/austin/tree/master/browser-connected-repl-sample)
that's included with [Austin](https://github.com/cemerick/austin) as a
starting point, then pulled in bits from
[cljs-liveedit-webapp](https://github.com/ejlo/cljs-liveedit-webapp)
until things worked. Figwheel's
[Flappy Bird Demo app](https://github.com/bhauman/flappy-bird-demo)
also provided some ideas. The concept of refreshing Om when Figwheel
reloads was taken from
[this blog post](http://blog.michielborkent.nl/blog/2014/09/25/figwheel-keep-Om-turning/)
by [Michiel Borkent](https://github.com/borkdude).

For Heroku support I looked at Heroku's
[clojure-getting-started](https://github.com/heroku/clojure-getting-started)
example app.

## License

Copyright © 2014-2016 Arne Brasseur

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.
