notes-on-grannycart-pages.md
Last modified: Thu Jul 29, 2021  02:38PM

# Notes on Grannycart pages
* First: most notes are actually in the grannycart pages in vimwiki
* This file is exclusively for how grannycart is set up in relation to nostyleplease
* (One of the tasks for grannycart is to write the documentation for how nostyleplease is set up for grannycart, this file is the rough start for that.)


## Things to do
* [ ] does the directory structure go in the root dir? or in _data?
	* how does a subdirectory work?

## index / home page
* It appears text in index.md is ignored by nostyleplease.
	* Instead index.md is used only to call the "home" page style
* The index / home page is actually configured in: 
	* _data/menu.yml

## layouts
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


