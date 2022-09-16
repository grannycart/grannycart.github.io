README.md
Last modified: Thu Sep 15, 2022  05:00PM

# README for grannycart web page
* By github.com/grannycart
* http://grannycart.github.io/
* Using theme: riggraz/no-style-please
	* https://github.com/riggraz/no-style-please
* NOTE: extended documentaion for site in [private github repo](../documentation/index.md).

## Setup google analytics with github pages theme that doesn't have it built in:
1. Create property on google analytics account
	* For now, when you create the property go into Advanced and create a UA property, not a G- property.
2. Get tracking codes from google analytics: Admin -> Property -> tracking info -> tracking code
3. Paste tracking code ("google site tag") into file: _includes/analytics.html
4. Check that your index.md YAML is set to use layout "home"
5. Edit _layouts/home.html and add {% include analytics.html %} above the </header> (This says to suck in that analytics.html file when rendering the page)
	* (I believe you have to repeat this step for any layout you use on the site)
6. Edit _config.yml and add google_analytics: UA-[custom tag from google]
	* (I think this is the only step necessary for themes that have google analytics support built in.)
* Note: UA- based google analytics will stop working in 2023. At that point you have to figure out how to make G- based properties work.

## License:
* Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
	* CC BY-NC-SA 4.0
	* See: [LICENSE](./LICENSE)






