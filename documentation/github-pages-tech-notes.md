documentation/github-pages-tech-Notes.md
Last modified: Mon Aug 02, 2021  04:05PM


--------------------------------------------------------------------------------
## Technical documentation (github website setup) with no-style-please theme
:techtips:
While github pages is super easy and fast if you are using a default theme,
setting it up with a custom theme (something I am interested in if I'm building
a long term repository for whatever "grannycart.net" becomes) turns out to be
phenomenally annoying and complicated. I feel like it's worth the effort
though because the heavy load in the beginning should, hopefully, in the
long-run make it very easy and quick to update and add stuff to the website.
(And having a low-barrier long term will make it much more likely I will keep
it up to date.) I also like that because it's built on a git repo I have a
local copy almost by default for posterity.

### Troubleshooting
* It appears text in index.md is ignored by nostyleplease.
	* Instead index.md is used only to call the "home" page style
* The index / home page is actually configured in: 
	* _data/menu.yml
* with github pages you need to commit and push any graphics/images for them to be on the server for github to serve
* if you waited a while and the page is not building, check the email associated with the github account for an error message
* it seems like sometimes to trigger pages to rebuild, you have to commit and push some minor edit (even just whitespace change) to the index.md file

### Files to set up in a new repo if you want it to look like yours, based on no-style-please:
* _config.yml
* _sass/no-style-please.scss
* _layouts/home.html
	* Possibly only need this for the top/menu page (see next 2 bullets)?
	* for grannycart, added: style="float:left; padding-right:20px;" to img tag to get the image to float next to the graphic. added width=300px too to limit image width
* assets/images/grannycart-logo.png
	* graphics that go on every pages should go in the assets dir
* _data/menu.yml
	* You only need this one for a site that uses the menu, like one that puts up posts
	* Not necessary for, like, bibliography. Or any other site/project that doesn't need the menu.

#### With no-style-please In every file:
* On most (all?) layouts the title: option will create an H1 header at the top of the page
	* (So no need to put a # Header at the beginning)
* Possible layouts are:
	* post
		* Top matter YAML for an archive page:
			---
			layout: post
			---
	* archive
		* Used for creating a grouping of posts (see riggraz/no-style-please)
		* Top matter YAML for an archive page:
			---
			layout: archive
			title: The title of the page here
			which_category: name-of-category
			---
	* default
	* home
	* page
		* Top matter YAML for a page:
			---
			layout: page
			title: The title of the page here
			---
* you need a little yaml at the top, like:
	---
	layout: post
	title: name of post
	---
	or
	---
	layout: home
	---
* On posts in particular, the title needs to be in the yaml because no-style-please puts the title in for you. layout: default gives you the blankest type of page.
* The three layout options are: home, default, and post
* This means you can't put your file name and Last modified: at the top of the page (that script that does that only looks in the first two lines, I think)

### Changing the background color
* Turned out to be a huge pain in the ass.
* I pretty quickly figured out that for the no-style-please theme the background color is set in the css which is pulled from:
	* _sass/no-style-please.scss
	* As the documentation indicates, just clone the no-style-please repo from the maintainer, and copy and override the _sass dir
	* So in that file you can make adjustments to the css, like color
	* You can also override _layouts and you might want to do that at some point.
* The problem I ran into, I think, was cloning the no-style-please repo and the copying the WHOLE thing into your local dir.
	* This must have been creating some kind of conflict between the local override files and the maintainers version
* Just build up your sites one file at a time.
* Get your _sass dir (and any other customizations you want) set and copy it into each repo you want to look like that.
* The delay in github pages building the page on their server adds to confusion
* And further confused by the recommendation to build your page locally before pushing it as a way to develop/test it.
	* This clearly gets you around github's delay-to-build issue
	* But it is not clear at all where the THEME is supposed to come from when you do that!
	* See notes in things that didn't work below about building test site for development
		* You might still want to try this when you do more serious site buildouts 

### On centering, and the problem with this whole github pages with a remotely maintained theme model
So I didn't work on my github pages site for a couple of months. And
when I came back to it, and wanted to copy dynohub.github.io github
pages (which I had painstakingly set up for colors, type, and visual
look-n-feel, though the content remained mostly the maintainer of the
no-style-please theme) to grannycart.github.io, to my utter confusion I
found that while on dynohub.github.io the content was centered on the
web page the way I wanted it, the exact copy in the grannycart.github.io
was running text from edge to edge.

It took an hour and a half of forensics to figure out that the
maintainer of no-style-please had changed the .wrapper element in the
_sass/no-style-please.css file to be a .w element. So my previous
.wrapper element was not overriding the new .w element. What was
endlessly frustrating is that dynohub.github.io _remembered_ the
previous wrapper element and looked fine. It was only when I pushed
the basically unchanged content for dynohub.github.io back up to the
github repo that it started to behave the same way as the exact copy at
grannycart.github.io did.

The process for figuring this out was to painstakingly copy one file
at a time from dynohub.github.io over to grannycart.github.io and push
each, then wait for github to publish the page, and see if the
centering when out of wack. grannycart.github.io stayed centered until
I pushed _sass/no-style-please.css (which, honestly should have been
the first one I tried). Then I cloned a new copy of the maintainer's
_sass/no-style-please.css file and compared them, and did some reading
on how .wrappers or .w containers are the thing that control the text
line wrap. The maintainers new code looks like more a more pro syntax,
but this is an incredibly frustrating thing to have to debug and makes
me very unhappy with github pages.


### Notes on using git
* See: my command line cheatsheet in wiki

### Fonts
* Font size can be changed in css file in _sass/no-style-please.scss
	* Just change the sizes in these two lines:
		* font-size: 1.3rem;
		* line-height: 1.3;
	* Note: Going down to 1 made block text too tight (see posts examples from maintainer at that size)
* font-family in _sass/no-style-please.csss adjusts fonts
* As always, fonts are totally fucked on the internet; so you should list a couple of different types in case one is not available
* It would be cool to go Courier, but that seems to only work in Firefox, not Chrome.
* Going to go with this font stack for now:
	* font-family: "Courier 10 Pitch", Courier, "Courier New", monospace;
* Colors from tumblr:
	* Background: #000000
	* Text: #c0c0c0 (I believe I set this to match the gray color I want)
	* Link: #0099bb
* Colors to try:
	* Off-black #313639
	* From Moria vim style:
		* background: #202020
		* Text: #d0d0d0
		* Line number: #8fa5d1

### Images
* You have to use a unspecified path like:
	*   <img alt="An exploded graphic of a Stumey-Archer internally geared AG dynohub" src="assets/images/sturmey-AG.png">
	* Don't forget you can include height and width specifications in the image tag if you need them

### Menu
* See:
	* in _data/menu.yml
		* (takes the place of index.md)
	* https://github.com/riggraz/no-style-please#customize-the-menu

## Favicon
* Generated from a drag-and-drop online favicon generator site
	* https://favicon.io/ 
* assets/favicons dir just contains alternate (currently unused) favicon types.
* favicon.ico is in home dir as the actual favicon




