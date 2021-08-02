documentation/tech-notes_didnt-work.md
Last modified: Mon Aug 02, 2021  03:25PM

# Github Pages Tech Notes: things that didn't work

### Experiment with adding css to assets/css/main.scss
	* Which is the file that pulls the stuff from the _sass dir. Who the fuck knows what is going on there.
	* You can add css below the import theme line; and that is supposed to override the css from the theme.
	* This didn't work for me on my local copy
	* I could see in developer tools while looking at the page that it was pulling the css from the developer's site instead of my own.

### Experiment with making my own theme:
* I tried making my own repo version of no-style-please and in _config.yml I pointed my repo to use that theme on github: grannycart/no-style-please
	* Changes the background color to black, the text to white
	* In THAT theme dir, I overrode the css in assets/css/main.scss and THAT seemed to work... at least once. I can't seem to get it to pick up any further changes.

### Compiling with jekyll and running and testing the site locally
* This stuff wasn't necessary. Hold onto for reference.
* Had to install ruby and jekyll. Just look up how to do that on the internet.
* Then I believe I did a gem install bundler. bundle is some software that does something with jekyll and ruby.
* Since ruby got installed to .gem I had to include it's bin path in my path:
	* set PATH ~/.gem/ruby/2.7.0/bin/ $PATH
* And then I could git clone no-style please and in the dir run:
	* bundle exec jekyll serve
	* And that would build the site and run a little web server where you could check out what the site looks like.
	* Creates _site dir with the compiled site files in it
		* LOCALLY changing the colors in _sass/no-style-please.scss and them compiling the site works.
		* These settings are in _site/assets/css/main.css
		* But pushing this build to github obviously won't affect the theme...
* It seems that jekyll themes are bundled into jems that are then served from rubygems.org
	* Not sure at all if this is still true for github pages; the gems might be served from the github repo of the maintainers?
	* But the idea is that the maintainer maintains the theme --- not you with a local copy.
	* See: https://jekyllrb.com/docs/themes/
	* That jekyll themes site indicates that for a theme you can override any file in the theme --- as long as you can figure out what file that theme gem is referencing





