# [Bootstrap](http://getbootstrap.com)

[![Slack](https://bootstrap-slack.herokuapp.com/badge.svg)](https://bootstrap-slack.herokuapp.com)
![Bower version](https://img.shields.io/bower/v/bootstrap.svg)
[![npm version](https://img.shields.io/npm/v/bootstrap.svg)](https://www.npmjs.com/package/bootstrap)
[![Build Status](https://img.shields.io/travis/twbs/bootstrap/master.svg)](https://travis-ci.org/twbs/bootstrap)
[![devDependency Status](https://img.shields.io/david/dev/twbs/bootstrap.svg)](https://david-dm.org/twbs/bootstrap#info=devDependencies)
[![Selenium Test Status](https://saucelabs.com/browser-matrix/bootstrap.svg)](https://saucelabs.com/u/bootstrap)

Bootstrap is a sleek, intuitive, and powerful front-end framework for faster and easier web development, created by [Mark Otto](https://twitter.com/mdo) and [Jacob Thornton](https://twitter.com/fat), and maintained by the [core team](https://github.com/orgs/twbs/people) with the massive support and involvement of the community.

To get started, check out <http://getbootstrap.com>!

## Table of contents

* [AdColony Specifics](#adcolony-specifics)
* [Quick start](#quick-start)
* [Bugs and feature requests](#bugs-and-feature-requests)
* [Documentation](#documentation)
* [Contributing](#contributing)
* [Community](#community)
* [Versioning](#versioning)
* [Creators](#creators)
* [Copyright and license](#copyright-and-license)

## AdColony Specifics

This is a branch of the Bootstrap 3.3.5 project specifically for setting up AdColony's core site styles.  Follow the [Quick start](#quick-start) guide to get set up.  Once you've got the repo ready you can build all the css by running `grunt adcolony`.  The default `grunt` build option will also set up a watch task.  The rest of this section will explain the structure and key components of the adcolony css.

### Directory structure 

AdColony bootstrap directory structure:

```
bootstrap/
└── adcolony/
    ├──css/ (css compiled by grunt build)
    ├──less/
    │   ├── mixins/ (Adcolony specific less mixins here)
    │   ├── adcolony-bootstrap.less (Primary less file)
    │   ├── adcolony-buttons.less (Button overrides and styles)
    │   ├── adcolony-core.less (Core styles)
    │   ├── adcolony-forms.less (Form related overrides and styles)
    │   ├── adcolony-grid.less (Grid definition)
    │   ├── adcolony-modal.less (Modal styles)
    │   ├── adcolony-scaffolding.less (Scaffolding/html structural styles)
    │   ├── adcolony-type.less (Font/type related overrides and style)
    │   └── adcolony-variables.less (Variable definitions and overrides)
    ├── html/
    │   └── index.html (Test file)
    └── fonts/
        ├── Lato-*.ttf (Primary font)
        └── freight-*/FreigSanPro*.otf (Header font)
```

### How to use this project

The different AdColony specific less files more or less mirror the structure of the main bootstrap project.  Button styles in a buttons file, form and input styles in a forms file, etc.  Any custom classes that are universal/reusable within the AdColony styling go into the 'core' file.  If you need to define a class for something specific to your project then it probably doesn't belong in here.  If it's a generic class that might have uses outside of your project then this is a good place for it.

The `index.html` file under the `html` folder is for testing styles, make use of it for quick testing.

### Key style rules

A lot of the style rules are defined within the `adcolony-variables.less` file, the most important ones will be covered here.

#### The grid

The grid used is a complete override of the bootstrap grid, though it follows a similar structure and uses the same class names.  The grid rules are:

* 1280px wide non-responsive container with 80px padding on left and right, top and bottom margins and a 1px border
* 12 columns with 20px padding on the right (calculated width of each column comes out to ~73px)

Other classes:
* `.row-full` - A row that takes up the full width of the container (including the 80px padding)
* `.inner-container` - A container that can be put inside another container and sits 40px inside of it with 40px padding

Check out `adcolony-grid.less` and `mixins/adcolony-grid.less` for more details.

#### Padding and Margins

Most spacing is based on a 4px system.  New classes should try to set up padding and margins on that 4px scale. (Use variable `@padding-scale`)

#### Font Styles and Sizes

The default style uses font family is Lato, weight regular, color `@gray-dark`, and size 13px

Defined Weights for Lato (all weights have an italics variation):
* `900` - Lato Black
* `bold` - Lato Bold
* `normal` - Lato (*Default)
* `300` - Lato Light
* `100` - Lato Hairline

Header styles use the Freight font family, weight semi-bold, color `@gray-dark`

Defined Weights for Freight (all weights have an italics variation):
* `900` - Freight Black
* `bold` - Freight Bold
* `500` - Freight Semi-Bold (*Default)
* `normal` - Freight Medium
* `300` - Freight Book
* `100` - Freight Light

Font sizes from smallest to largest: 

* 11px (`.text-small`, used by `<h5>`)
* 13px (standard font-size, used by `<h4>`)
* 16px (`.text-large`, used by `<h3>`)
* 21px (`<h2>`)
* 24px (`<h1>`)

#### Colors

Gray Colors
* `@gray-darker:             #455864;`
* `@gray-dark:               #546e7a;`  (Default text color)
* `@gray:                    #90a4ae;`  (`.text-muted`)
* `@gray-light:              #b0bec5;`  (`.text-muted-light`)
* `@gray-lighter:            #cfd8dc;`  (Used by grid border)
* `@gray-lightest:           #eceff1;`  (Used by `<hr>`)

Other Colors (Outside of primary these values haven't been locked down)
* `@brand-primary:         #51B2EF;`
* `@brand-success:         #66BB6A;`
* `@brand-info:            #5bc0de;`
* `@brand-warning:         #FFECB3;`
* `@brand-danger:          #FF7043;`

## Quick start

Several quick start options are available:

* [Download the latest release](https://github.com/twbs/bootstrap/archive/v3.3.5.zip).
* Clone the repo: `git clone https://github.com/twbs/bootstrap.git`.
* Install with [Bower](http://bower.io): `bower install bootstrap`.
* Install with [npm](https://www.npmjs.com): `npm install bootstrap`.
* Install with [Meteor](https://www.meteor.com): `meteor add twbs:bootstrap`.
* Install with [Composer](https://getcomposer.org): `composer require twbs/bootstrap`.

Read the [Getting started page](http://getbootstrap.com/getting-started/) for information on the framework contents, templates and examples, and more.

### What's included

Within the download you'll find the following directories and files, logically grouping common assets and providing both compiled and minified variations. You'll see something like this:

```
bootstrap/
├── css/
│   ├── bootstrap.css
│   ├── bootstrap.css.map
│   ├── bootstrap.min.css
│   ├── bootstrap.min.css.map
│   ├── bootstrap-theme.css
│   ├── bootstrap-theme.css.map
│   ├── bootstrap-theme.min.css
│   └── bootstrap-theme.min.css.map
├── js/
│   ├── bootstrap.js
│   └── bootstrap.min.js
└── fonts/
    ├── glyphicons-halflings-regular.eot
    ├── glyphicons-halflings-regular.svg
    ├── glyphicons-halflings-regular.ttf
    ├── glyphicons-halflings-regular.woff
    └── glyphicons-halflings-regular.woff2
```

We provide compiled CSS and JS (`bootstrap.*`), as well as compiled and minified CSS and JS (`bootstrap.min.*`). CSS [source maps](https://developer.chrome.com/devtools/docs/css-preprocessors) (`bootstrap.*.map`) are available for use with certain browsers' developer tools. Fonts from Glyphicons are included, as is the optional Bootstrap theme.



## Bugs and feature requests

Have a bug or a feature request? Please first read the [issue guidelines](https://github.com/twbs/bootstrap/blob/master/CONTRIBUTING.md#using-the-issue-tracker) and search for existing and closed issues. If your problem or idea is not addressed yet, [please open a new issue](https://github.com/twbs/bootstrap/issues/new).


## Documentation

Bootstrap's documentation, included in this repo in the root directory, is built with [Jekyll](http://jekyllrb.com) and publicly hosted on GitHub Pages at <http://getbootstrap.com>. The docs may also be run locally.

### Running documentation locally

1. If necessary, [install Jekyll](http://jekyllrb.com/docs/installation) (requires v2.5.x).  
   **Note for Windows users:** Read [this unofficial guide](http://jekyll-windows.juthilo.com/) to get Jekyll up and running without problems.
2. Install the Ruby-based syntax highlighter, [Rouge](https://github.com/jneen/rouge), with `gem install rouge`.
3. From the root `/bootstrap` directory, run `jekyll serve` in the command line.
4. Open `http://localhost:9001` in your browser, and voilà.

Learn more about using Jekyll by reading its [documentation](http://jekyllrb.com/docs/home/).

### Documentation for previous releases

Documentation for v2.3.2 has been made available for the time being at <http://getbootstrap.com/2.3.2/> while folks transition to Bootstrap 3.

[Previous releases](https://github.com/twbs/bootstrap/releases) and their documentation are also available for download.



## Contributing

Please read through our [contributing guidelines](https://github.com/twbs/bootstrap/blob/master/CONTRIBUTING.md). Included are directions for opening issues, coding standards, and notes on development.

Moreover, if your pull request contains JavaScript patches or features, you must include [relevant unit tests](https://github.com/twbs/bootstrap/tree/master/js/tests). All HTML and CSS should conform to the [Code Guide](https://github.com/mdo/code-guide), maintained by [Mark Otto](https://github.com/mdo).

Editor preferences are available in the [editor config](https://github.com/twbs/bootstrap/blob/master/.editorconfig) for easy use in common text editors. Read more and download plugins at <http://editorconfig.org>.



## Community

Get updates on Bootstrap's development and chat with the project maintainers and community members.

* Follow [@getbootstrap on Twitter](https://twitter.com/getbootstrap).
* Read and subscribe to [The Official Bootstrap Blog](http://blog.getbootstrap.com).
* Join [the official Slack room](https://bootstrap-slack.herokuapp.com).
* Chat with fellow Bootstrappers in IRC. On the `irc.freenode.net` server, in the `##bootstrap` channel.
* Implementation help may be found at Stack Overflow (tagged [`twitter-bootstrap-3`](https://stackoverflow.com/questions/tagged/twitter-bootstrap-3)).
* Developers should use the keyword `bootstrap` on packages which modify or add to the functionality of Bootstrap when distributing through [npm](https://www.npmjs.com/browse/keyword/bootstrap) or similar delivery mechanisms for maximum discoverability.



## Versioning

For transparency into our release cycle and in striving to maintain backward compatibility, Bootstrap is maintained under [the Semantic Versioning guidelines](http://semver.org/). Sometimes we screw up, but we'll adhere to those rules whenever possible.

See [the Releases section of our GitHub project](https://github.com/twbs/bootstrap/releases) for changelogs for each release version of Bootstrap. Release announcement posts on [the official Bootstrap blog](http://blog.getbootstrap.com) contain summaries of the most noteworthy changes made in each release.



## Creators

**Mark Otto**

* <https://twitter.com/mdo>
* <https://github.com/mdo>

**Jacob Thornton**

* <https://twitter.com/fat>
* <https://github.com/fat>



## Copyright and license

Code and documentation copyright 2011-2015 Twitter, Inc. Code released under [the MIT license](https://github.com/twbs/bootstrap/blob/master/LICENSE). Docs released under [Creative Commons](https://github.com/twbs/bootstrap/blob/master/docs/LICENSE).
