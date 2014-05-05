Static Site Boilerplate
=======================

This boilerpate code is a [Jekyll](http://jekyllrb.com/) static site, was created with [Yeoman](http://yeoman.io/) using [generator-jekyllrb](https://github.com/robwierzbowski/generator-jekyllrb). You can manage front end packages with [Bower](http://bower.io/), and automate development and build tasks with [Grunt](http://gruntjs.com/).


## How to use this?

1. Clone this repository `git clone https://github.com/mariusmateoc/static-site-boilerplate`
2. Install node dependencies `npm install`
3. Install bower dependencies `bower install`
4. Install bundler dependencies `bundle install`
5. Simply run `grunt serve` to see that everything works

**Require**

- [Node.js](http://nodejs.org/) `>= 0.10`, [Ruby](http://www.ruby-lang.org/) `>= 1.9`, and the [Bundler](http://gembundler.com/) gem


## Features

- [Compass](http://compass-style.org/), [Sass](http://sass-lang.com/), or vanilla CSS
- [Susy](http://susy.oddbird.net/) for Grids
- [Breakpoint-Sass](http://breakpoint-sass.com/) for Media Queries
- Automatic CSS vendor prefixing with [Autoprefixer](https://github.com/ai/autoprefixer)
- [HTML5 Boilerplate](http://html5boilerplate.com/) template

**Boilerplate includes:**

- Built in preview server with LiveReload
- Automatic Jekyll and preprocessor compiling
- An automatic build process that includes concatenation, image optimization, CSS and HTML minification and JS uglification.


## Grunt Workflow

#### grunt serve

Compiles all files and opens the site in your default browser. A watch task watches for changes to files, recompiles if necessary, and injects the changes into the browser with LiveReload.

#### grunt build

Builds an optimized site to the dist directory. [Usemin blocks](https://github.com/yeoman/grunt-usemin#the-useminprepare-task) are concatenated, [CSS](https://github.com/gruntjs/grunt-contrib-cssmin), [images](https://github.com/gruntjs/grunt-contrib-imagemin), and [HTML](https://github.com/gruntjs/grunt-contrib-htmlmin) are minified, [JavaScript is uglified](https://github.com/gruntjs/grunt-contrib-uglify), and assets are [revved](https://github.com/yeoman/grunt-filerev) for cache busting.

`grunt serve:dist` will run `grunt build` and open the result in your default browser

#### grunt (default)

`grunt` on its own is a special task that runs `grunt check`, any tests you've added, and `grunt build`.


## Bower, components, and Usemin

[Bower](http://bower.io/) is a package manager for front-end components. Use it to download and manage CSS, JavaScript, and [preprocessor tools](https://github.com/Team-Sass) for your site. Everything in the _bower_components directory is available while running `grunt serve`.

To include components in the build, place them inside of a Usemin block or add them to the `copy:dist` task. This workflow will be streamlined with the release of Usemin 2.0.


## Notes

#### Nested asset directories and Jekyll

Jekyll [can't exclude nested directories](https://github.com/jekyll/jekyll/issues/906), so we must exclude all directories that match the innermost asset directory. For example, `assets/css` will exclude all directories named `css` from Jekyll compilation. This will cause issues if your site has a tag or category named `css`; if you're worried about accidental exclusions prefix all asset directories with an underscore (`assets/_css`).

#### Absolute path to assets in CSS

Since we revision assets such as images, make sure that your CSS calls them using their absolute path, so on ``grunt build`` those images will be replaced properly.

Incorrect:
```css
body {
  background: url('../images/foo.jpg');
}
```

Correct:
```css
body {
  background: url('/images/foo.jpg');
}
```
