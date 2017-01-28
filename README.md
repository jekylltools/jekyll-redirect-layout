# Jekyll Redirect Layout

Jekyll layout to create URL redirects in pure Liquid. No plugin needed.

## Installation

1. Add `_layouts/redirect.html` to your `_layouts` folder.

2. Create a `_redirects` folder in your Jekyll root folder.

3. Add the following to your `_config.yml`:

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

Set `canonical` to `true` if you want to indicate the destination is the canonical URL for this redirect.

**`prepend`** _(optional. defaults to false)_

Set `prepend` to `true` if you want to add `site.url` in front of the destination URL. Leave this false if you are redirecting to an external URL.

If you are using a sitemap generator, you generally want to exclude all redirects from your sitemap. Usually this is done by adding `sitemap: false` as a front-matter variable.

## Examples

There are more examples located in the `_redirects` folder.

An example internal redirect:

```
---
permalink: /redirect-this-url/
destination: /to-this-location/
canonical: true
prepend: true
---
```

An example external redirect:

```
---
permalink: /leaving/
destination: http://example.com/arriving
canonical: false
prepend: false
---
```

## Support

[Open an issue](https://github.com/xHN35RQ/jekyll-redirect-layout/issues) if you have any problems, questions or suggestions for improvement.