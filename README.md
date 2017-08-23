# Jekyll Redirect Layout

Jekyll layout to create URL redirects with HTML and JavaScript. No plugin necessary.

Generates Javascript redirects with fall back to meta refresh redirects. Fully compatible with Github Pages.

View a [live demo running on Github Pages](https://jekylltools.github.io/jekyll-redirect-layout/examples/). The code and configuration for the demo is in the [gh-pages branch](https://github.com/jekylltools/jekyll-redirect-layout/tree/gh-pages).

## Installation

1. Add `_layouts/redirect.html` to the `_layouts` folder.

2. Create a `_redirects` folder in the Jekyll root folder.

3. Add the following to `_config.yml`. This adds the `redirects` collection to Jekyll and sets the default layout for the collection to `_layouts/redirect.html`:

	```
	collections:
	  redirects:
	    output: true

	defaults:
	  -
	    scope:
	      type: redirects
	    values:
	      layout: redirect
	```

## Usage

A redirect is a Jekyll page which redirects the browser to a new location. Redirect files are added to the `_redirects` folder and use the redirect layout by default.

Configure each redirect with front-matter variables:

**`permalink`** _(required)_

The permalink is the URL of the redirect. For example:

```
permalink: /redirect-this-url/
```

**`destination`** _(required)_

The destination is the URL to which the browser will be redirected. For example:

```
destination: /to-this-location/
```

**`canonical`** _(optional. defaults to false)_

Set `canonical` to `true` to indicate the destination is the canonical URL for this redirect.

When using a sitemap generator, it is common to exclude all redirects from the sitemap. Usually this is done by adding `sitemap: false` as a front-matter variable.

## Examples

There are more examples located in the `_redirects` folder.

An example internal canonical redirect:

```
---
permalink: /redirect-this-url/
destination: /to-this-location/
canonical: true
---
```

An example external redirect:

```
---
permalink: /leaving/
destination: http://example.com/arriving
canonical: false
---
```
