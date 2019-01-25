# Etoile is a premium blogging Jekyll theme

Etoile was developed by [PressApps](https://pressapps.co), theme [live demo](https://etoile.jekyll.plus/) available.

## Features

* Live Search
* Image lightbox
* Contact form (FormSpree)
* Image lightbox and slider
* Disqus comments for posts
* Configurable home page
* Optimised for [GitHub](https://pages.github.com/) pages
* RSS feed
* SEO tags
* Google Analytics


## Installation

Install the dependencies with [Bundler](http://bundler.io/):

```bash
bundle install
```

Run the following to generate your site:
```bash
bundle exec jekyll serve
```

You can find more on [Deployment Methods](https://jekyllrb.com/docs/deployment-methods/) page on Jekyll website.

## Setup

### Site and author details
Add your site and author details in `_config.yml`:
```yaml
# Site settings
title:              Étoile
description:        Magazine Jekyll theme for writers and bloggers.
url:                # Site base hostname & protocol, e.g. http://example.com
baseurl:            "" # Site subpath, e.g. /blog
logo_image:
  dark:             # Dark logo e.g logo-dark.svg upload to /uploads/ folder, used in header, mobile navigation and page sidebar About widget
  light:            # Light logo e.g. logo-light.svg upload to /uploads/ folder, used in footer About widget
permalink:          /:title/ # Permalink URLs structure, for permalink style options see: https://jekyllrb.com/docs/permalinks/
date_format:        "%B %-d, %Y" # refer to http://shopify.github.io/liquid/filters/date/ if you want to customize this
uploads:            /uploads/ # Path to post content assets directory i.e post images, pdfs etc
paginate:           7 # Number of posts displayed on blog page
paginate_path:      "/blog/:num/" # Blog path
google_analytics:   # Google analytics code, get your code here https://www.google.com/analytics/
disqus:
  shortname:        # Disqus comments shortname, requires Disqus account https://disqus.com/

instagram_accesstoken: # Generate token here: http://instagram.pixelunion.net/

footer:             # Default footer image settings
  copyright:        Made by a <a href="https://ivanchromjak.com/">human</a> somewhere on the planet earth.
```

### Navigation Bar
Set in the main navigation links in `_data/navbar_primary.yml`:
```yaml
- title: About
  url: /about/
```

### Widgets
Set in the page sidebar and footer sidebar widgets in `_data/sidebars.yml`. Chose from the following widgets: `categories`, `recent`, `authors`, `about`, links. Edit copyright notice in about widget in `_config.yml`:
```yaml
footer:
    copyright:
```

### Enabling comments (via Disqus)

Optionally, if you have a Disqus account, you can tell Jekyll to use it to show a comments section below each post. To enable it, add the following lines to your Jekyll site:

```yaml
disqus:
    shortname: my_disqus_shortname
```

You can find out more about Disqus' shortnames [here](https://help.disqus.com/customer/portal/articles/466208).

Comments are enabled by default and will only appear in production, i.e., `JEKYLL_ENV=production`. If you don't want to display comments for a particular post you can disable them by adding `comments: false` to that post's YAML Front Matter.

### Google Analytics

To enable Google Anaytics, add the following lines to your Jekyll site:

```yaml
  google_analytics: UA-NNNNNNNN-N
```

Google Analytics will only appear in production, i.e., `JEKYLL_ENV=production`

### Contact Form (via FormSpree)

Submit the form and confirm your email address at [FormSpree](https://formspree.io/). Then add the following code to page content:

```
{% include formspree.html email="my_name@gmail.com" redirect="/thanks/" %}
```

### Update favicon

You can find the current favicon (favicon.png) inside the theme `/uploads/` directory, just replace it with your new favicon.

## Posts

To create a new post, you can create a new markdown file inside the `_posts` directory by following the recommended file naming format:
```
YEAR-MONTH-DAY-title.MARKUP
```
Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. For example, the following are examples of valid post filenames:

```
2011-12-31-new-years-eve-is-awesome.md
2012-09-12-how-to-write-a-blog.md
```

Post requires front matter, everything in between the first and second --- are part of the YAML Front Matter, and everything after the second --- will be rendered with Markdown and show up as “Content”.
The following is a post file with different configurations you can add as example:

```yaml
---
title: Best tech companies to work for in 2019
image: post-image.jpg       # Upload the image to uploads directory
categories: [business]      # Same as category post tag
tag: [spotlight, featured]  # Optional: spotlight tag adds post to spotlight section, featured tag add post to featured section
hidden: true                # Optional: exlude the post from blog page posts
author: sarah               # Reference author username
---
```

You can rebuild the site in many different ways, but the most common way is to run `bundle exec jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To keep things more organized you can organize post images in subdirectiories e.g. `/uploads/2019/01/`.

### Adding images
To add an image to a post or page use the following codes:
Local image from `/uploads/` directory:
```yaml
{% include image.html img="girl.jpg" alt="Alt for image" caption="Girl on a rock" %}
```
External wide image with lightbox:
```yaml
{% include image.html img="https://source.unsplash.com/TT-ROxWj9nA.jpg" lightbox="true" alt="Alt for image" caption="Image in lightbox" %}
```

### Responsive Videos
Embed local videos:
```html
<video controls playsinline uk-video="automute: true">
    <source src="http://www.quirksmode.org/html5/videos/big_buck_bunny.mp4" type="video/mp4">
    <source src="http://www.quirksmode.org/html5/videos/big_buck_bunny.ogv" type="video/ogg">
</video>
```
Embed YouTube videos:
```html
<iframe src="http://www.youtube.com/embed/YE7VzlLtp-4?autoplay=0&amp;showinfo=0&amp;rel=0&amp;modestbranding=1&amp;playsinline=1" width="600" height="340" frameborder="0" allowfullscreen uk-responsive uk-video="automute: true"></iframe>
```

To create a draft post, create the post file under the `_drafts` directory, and you can find more information in [Working with Drafts](https://jekyllrb.com/docs/drafts/).

## Home Page

To create a home page, just create a `index.md` file inside the root directory. The following is a YAML Front Matter example for a page:

```yaml
---
layout: full
---
```

Home page sections are created using includes that can be easily rearranged and modified, e.g.:
```
{% include section-ad.html image="welcome.png" alt="Buy Étoile Jekyll Theme" width="" url="https://themeforest.net/user/pressapps/portfolio" blank="true" %}

{% include section-featured.html title="Featured Story" %}

{% include section-spotlight.html title="Spotlight" %}

{% include section-mailchimp.html title="Newsletter Signup" text="Sign up for our weekly newsletter through Mailchimp and stay up to date with what is happening in the city." button_text="Support Us" %}

{% include section-latest.html title="Latest Articles" limit="4" more="More Articles" %}

{% include section-ad.html title="Advertisement" image="https://via.placeholder.com/800x180/f4f4f4/fff.png?text=+" url="#" blank="true" %}

{% include section-authors.html title="Our Contributors" %}

{% include section-instagram.html title="Latest On Instagram" cols="4" count="4" gutter="true" %}

{% include section-cta.html title="Want To Contribute?" text="We are looking for writers from all walks of life to contribute to out blog, if you have something to say get in touch." button_text="Contact Us" button_url="/contact/" blank="true" %}

{% include section-author.html author="john" title="Hello, I am Jane! Welcome to my blog." %} 
```

## Authors

To create an author, create a new post inside the `_authors` directory and add the following YAML Front Matter:
```
---
title:          John Nolten
username:       john
image:          avatar_john.jpg
bio:            Writer at WorkBox Publishing, parent, aminal lover and avid coffee drinker.
email:          me@mysite.com
website:        https://mysite.com
facebook:       https://www.facebook.com/
flickr:         https://www.flickr.com/
dribbble:       https://dribbble.com/
github:         https://github.com/
reddit:         https://www.reddit.com/
instagram:      https://www.instagram.com/
linkedin:       https://www.linkedin.com/
pinterest:      https://www.pinterest.com
twitter:        https://twitter.com/
vimeo:          https://vimeo.com/
youtube:        https://www.youtube.com/
---
```

Add post content and upload author `avatar_john.jpg` avatar to `uploads` folder.

## Categories

To create a category, create a new post inside the `_category` directory and add the following YAML Front Matter:
```
---
tag: business
permalink: "/category/business/"
---
```

## Customization

To modify the primary color, open `/assets/css/main.scss` and replace the `#de7a93` color value:
```scss
// Modify primary template color
$global-primary-background: #de7a93;
```

To modify the fonts, open `/assets/css/main.scss` and modify the following values:
```scss
// Modify body font
$global-font-family: 'Lora', serif; 
// Modify article title font
$aticle-title-font-family: 'ZCOOL XiaoWei', serif;
```

Edit the embedded Google fonts in `/_includes_/head-custom.html`.

Further style customisation can be done in the following files:
```
/_sass/theme/mixins.scss
/_sass/theme/variables.scss
/assets/css/main.scss
```

## Development

Install [UIkit](https://getuikit.com/) font end framework dependency via Npm:
```bash
npm install
```
Enable live browser reload with the following:
```bash
bundle exec jekyll s --livereload
```

## Credits and Sources

- Google analytics https://www.google.com/analytics/
- UIkit front end framework https://getuikit.com/
- Unsplash images https://unsplash.com/
- Jekyll CML https://jekyllrb.com/

## Support
Customer support is provided through our Envato profile page [contact form](https://themeforest.net/user/pressapps) for up to six months from the purchase date and is provided Monday to Friday during the business week. We aim to answer all support requests daily, most are handled within 48h.
