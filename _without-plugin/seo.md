---
title: SEO
---

### Introduction

WordPress is famous for its SEO plugin. But what does it exactly do? Little that cannot be achieved by some HTML and liquid. This script takes care of the following things in the head:

- title
- meta description
- shortcut icons
- open graph tags
- canonical link
- [atom feed](/without-plugin/atom-feed)
- [sitemap](/without-plugin/sitemap)

### How it works

The following code adds all these items to your head:

```
{% raw %}<meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1">

<title>{% if page.title %}{{ page.title }} | {% endif %}{{ site.title }}</title>
<meta name="description" content="{{ page.content | strip_html | strip_newlines | truncate: 160 }}">

<link rel="shortcut icon" type="image/png" href="/img/icon-196x196.png">
<link rel="shortcut icon" sizes="196x196" href="/img/icon-196x196.png">
<link rel="apple-touch-icon" href="/img/icon-196x196.png">

<!-- Facebook and Twitter integration -->
<meta property="og:title" content="{{ page.title }}"/>
{% if page.image %}<meta property="og:image" content="{{ page.image }}"/>{% endif %}
<meta property="og:url" content="{{ page.url }}"/>
<meta property="og:site_name" content="{{ site.title }}"/>
<meta property="og:description" content="{{ page.content | strip_html | strip_newlines | truncate: 160 }}"/>
<meta name="twitter:title" content="{{ page.title }}" />
{% if page.image %}<meta name="twitter:image" content="{{ page.image }}" />{% endif %}
<meta name="twitter:url" content="{{ page.url }}" />
<meta name="twitter:card" content="{{ page.content | strip_html | strip_newlines | truncate: 160 }}" />

<link rel="canonical" href="{{ page.url | replace:'index.html','' | prepend: site.baseurl | prepend: site.url }}">
<link rel="alternate" type="application/rss+xml" title="{{ site.title }}" href="{{ "/feed.xml" | prepend: site.baseurl | prepend: site.url }}">
<link rel="sitemap" type="application/xml" title="Sitemap" href="{{ "/sitemap.xml" | prepend: site.baseurl | prepend: site.url }}" />{% endraw %}
```

Note: Ofcourse you can also set manual page descriptions, using 'page.description' and a matching YML variable in your page. 

### Installation

Step 1. Download the file [head.html](https://raw.githubusercontent.com/jhvanderschee/jekyllcodex/gh-pages/_includes/head.html)
<br />Step 2. Save the file in the '_includes' directory of your project
<br />Step 3. Make sure the structure of your layout document looks like this:

```
{% raw %}<!DOCTYPE html>
<html>
<head>
{% include head.html %}
</head>
<body>
...{% endraw %}
```
