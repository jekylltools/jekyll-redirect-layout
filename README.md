# Jekyll Redirect Layout

Jekyll layout to create URL redirects in pure Liquid. No plugin needed.

## Installation

Add `_includes/redirect.html` to your `_includes` folder.

## Usage

A redirect is Jekyll page which redirects the browser to a new location. We configure each redirect with front-matter variables. Then we use Liquid code to include the redirect layout and pass the variables to it.

### 1. Set front-matter variables

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

**`canonical: true/false`** _(optional. defaults to false)_

Set `canonical` to true if you want to indicate the destination is the canonical URL for this redirect.

**`prepend: true/false`** _(optional. defaults to false)_

Set `prepend` to true if you want to add `site.url` in front of the destination URL. Leave this false if you are redirecting to an external URL.

If you are using a sitemap generator, you generally want to exclude all redirects from your sitemap. Usually this is done by adding `sitemap: false` as a front-matter variable.

### 2. Include redirect layout

Use this Liquid code to include the redirect layout and pass the front-matter variables to it:

```
{% include redirect.html canonical=page.canonical destination=page.destination prepend=page.prepend %}
```

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
{% include redirect.html canonical=page.canonical destination=page.destination prepend=page.prepend %}
```

An example external redirect:

```
---
permalink: /leaving/
destination: http://example.com/arriving
canonical: false
prepend: false
---
{% include redirect.html canonical=page.canonical destination=page.destination prepend=page.prepend %}
```

## Custom redirects folder

I recommend to organize all redirects into a single folder:

1. Create a `_redirects` folder in your Jekyll root folder
2. Add `include: [_redirects]` to your `_config.yml`

Jekyll will now include all files from `_redirects` when building your site. You can add sub-folders if you need more organization.

I also recommend to organize all pages into a single folder, leaving `index.html` and `404.html` in your root folder.

Adding this line to your `_config.yml` instructs Jekyll to include `_pages` and `_redirects` when building your site:

```
include: [_pages, _redirects]
```

## Support

[Open an issue](https://github.com/xHN35RQ/jekyll-redirect-layout/issues) if you have any problems, questions or suggestions for improvement.