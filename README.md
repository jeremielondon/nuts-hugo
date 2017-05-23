# Guide to the custom Nuts theme for Hugo

> Site ported from html to Hugo on 18/05/2017

> by Luke Spear - https://lukespear.co.uk | https://worldtowriters.com

## Getting started

1. Change the baseurl to your testing environment, check rest of config.toml
2. Build the site in latest Hugo build (built in 20.7).
3. Send yourself an email from the contact page to claim the form for your domain.
4. Test site + links

## Overview

A typical page on the hugo site in this theme looks like this:

1. Header partial -> header.html, includes nav bar and metadata

2. Banner partial -> msgbox.html, includes page title and image, set in yaml per 
page/post. Not included if blank or nobanner is set.

3. Page or blog content -> Pages directly under /content and blogs under /Blogs. 
Can be html or markdown. Variable/partial calls don't work here. Uses 
/layouts/_default/single.html for blog posts and /layouts/page/single.html for pages.

4. Disqus/sidebar partial -> Disqus comments appear under blog posts only. Sidebar 
appears on blog posts only.

5. Footer partial -> footer.html, includes a few links and language selectors

## Adding blog posts

Create a new file under /content/Blog with the filename.md or filename.fr.md for French.
Hugo knows the difference. Copy the metadata as per the other posts, between +++ markers.

To display these posts on the nutspubcrawl.com/blog-guide or French index page (that
has been converted from html to be language aware), you need to copy and paste a section. 
Alternatively, view the nutspubcrawl.com/fr/blog or /blog list page.

The layout for this list page is at themes/*/layouts/_default/list.html.

> NB: The other way we can do this is to make the list.html include the same icons and
> descriptions.

## Adding pages (i.e. the links in navbar)

As this was a port from html to hugo, and each page was different, we've kept the layout
of each original page in HTML. To create a new page, in HTML or otherwise, create an .md 
file in /content and its corresponding French version (filename.fr.md) in the same place.
Hugo will pick this up automatically.

Add the relevant links manually to the themes/*/layout/partials/header.html, following the 
existing format. This will let changes to /i18n/en.yaml and fr.yaml control the navbar 
depending on language context.

Depending on whether you want a banner or not, add the type = nobanner to the metadata of 
the page to use the template that is the same as the default, but without the banner.

## Adding translations

See the /i18n folder for the current languages. Modify the strings and run 'hugo' again to 
update.

To create a new string to translate, copy the format in the language files and call it in 
your templates by: {{ i18n "pageAbout" . }}

NOTE: you cannot call translations directly in the post/pages in the /content folder, 
at least afaik.

## Adding partials

Edit and add partials in the /themes/*/layouts/partials directory. Follow the format of the 
others, call them with the {{ partial "partialname.html" . }} call in any template.


