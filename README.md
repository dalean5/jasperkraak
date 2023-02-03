# Jasper Kraak's Personal Website + Blog

Jasper Kraak's personal website and blog

## Features
 - 100% Lighthouse scores
 - Toggleable dark theme (PS. theme preference is also stored in `localStorage`)
 - Tags as taxonomy
 - Stylus CSS preprocessor
 - Also generates Atom RSS Feed with Eleventy's official [RSS plugin](https://www.11ty.dev/docs/plugins/rss/)
 - Sitemap generation
 - Non-post pages support (eg. About page, Contact page)
 - Modular type scale implemented in with Stylus

## Url

 - Public URL: https://www.kraak.com


## How to publish a new blog post

Store the new post as a markdown file in the posts directly. Commit the changes and push the changes to Github. The site will build and deploy automatically.

```sh
git push .

git commit -m "commit message"

git push -u origin master
```
