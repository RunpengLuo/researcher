# runpengluo.github.io/researcher

Personal academic website of Runpeng (John) Luo, built with [Jekyll](https://jekyllrb.com) and published by GitHub Pages from the `gh-pages` branch at <https://runpengluo.github.io/researcher>.

The design is derived from the [researcher](https://github.com/ankitsultana/researcher) theme by Ankit Sultana; the layouts in `_layouts/` and styles in `_sass/` are vendored into this repository, so no theme gem is used.

## Table of Contents

- [Local development](#local-development)
- [Content layout](#content-layout)
- [Adding a blog post](#adding-a-blog-post)
- [Analytics and visitor map](#analytics-and-visitor-map)
- [License](#license)

## Local development

Ruby is managed with conda (the `compilers` package is required, otherwise the `eventmachine` native extension fails to build):

```sh
mamba create -y -n jekyll -c conda-forge ruby compilers
conda activate jekyll
bundle install
bundle exec jekyll serve --livereload   # http://127.0.0.1:4000/researcher/
```

`bundle exec jekyll build` writes the static site to `_site/`, which is ignored by git; GitHub Pages runs its own build on push.

## Content layout

| Path | Purpose |
| --- | --- |
| `index.md`, `resume.md`, `publications.md`, `softwares.md`, `blogs.md`, `contact.md` | Pages; each renders at `/researcher/<name>` |
| `_posts/` | Blog posts, listed automatically on the Blogs page |
| `_layouts/` | `default.html` (site chrome) and `post.html` (post title and date) |
| `_sass/`, `css/main.scss` | Styles; the hyperlink accent color is `$accent` in `_sass/vars.scss` |
| `files/` | CV PDF, profile photo, and notes under `files/docs/` |
| `_config.yml` | Site metadata and the `nav` list that drives the navigation bar |

Navigation entries come from `nav` in `_config.yml`. The entry named `About` is special-cased in `_layouts/default.html` and its `link` is used verbatim; every other entry is prefixed with the site URL and base URL.

## Adding a blog post

Create `_posts/YYYY-MM-DD-name.md` with front matter, and it appears on the Blogs page automatically:

```yaml
---
layout: post
title: "Post title"
date: 2024-03-23
location: Princeton, NJ, USA
---
```

## Analytics and visitor map

Page views are counted by [GoatCounter](https://www.goatcounter.com) (cookie-free); the script loads only when `goatcounter_code` is set in `_config.yml`.

The visitor map on the Contact page is built from that data by `.github/workflows/deploy.yml`:

1. A daily cron run calls `scripts/fetch_visitors.py`, which reads `/api/v0/stats/locations` with the `GOATCOUNTER_TOKEN` repository secret and writes `_data/visitors.yml`.
2. Jekyll builds the site and `_includes/visitor-map.html` shades `_includes/world-map.svg` per country.
3. `actions/deploy-pages` publishes the built site, so nothing is committed back to the repository.

This requires the repository's Pages publishing source to be set to **GitHub Actions** (Settings -> Pages -> Build and deployment -> Source).

`_includes/world-map.svg` was generated from [Natural Earth](https://www.naturalearthdata.com) 110m country data, which is in the public domain.

## License

[GNU GPL v3](LICENSE), inherited from the upstream theme.
