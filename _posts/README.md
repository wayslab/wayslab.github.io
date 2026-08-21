# How to Add a Publication

Publication pages are created from Markdown files in this directory. Jekyll uses
the date in the filename to sort the publication list.

## 1. Create the file

Use this filename format:

```text
YYYY-MM-DD-short-name.md
```

For example:

```text
2026-08-21-example-paper.md
```

Use a unique date and a short, readable name. Keep the file extension as `.md`.

## 2. Add the front matter

Start the file with YAML front matter between two `---` lines:

```yaml
---
layout: publication
title: "Full Paper Title"
short_title: "Short Name"
tags: Communications Wireless-Sensing
cover: /assets/images/pubpic/example-cover.png
authors: "First Author, Second Author, and Dinesh Bharadia"
conference: "ACM MobiCom 2026"
conference_site: https://example.org/conference
paper: /files/example-paper.pdf
slides: /files/example-slides.pdf
github: https://github.com/example/repository
video: https://www.youtube.com/embed/example-id
video_str: Demo
miscs:
  - content_type: Dataset
    content_url: https://example.org/dataset
highlight: false
---
```

Required fields:

- `layout`: Use `publication`.
- `title`: Full publication title.
- `short_title`: Short name used in list views.
- `tags`: Space-separated research tags. Match existing tag spelling.
- `cover`: Image path used on publication lists.
- `authors`: Author names as one comma-separated string.
- `conference`: Conference, journal, or workshop name.
- `paper`: Link to the paper PDF.

## 3. Add files

Store papers, slides, posters, and supplementary material in `/files`. Store
publication cover images in `/assets/images/pubpic`.

Use site-relative paths beginning with `/`:

```yaml
paper: /files/example-paper.pdf
slides: /files/example-slides.pdf
cover: /assets/images/pubpic/example-cover.png
```

External links can use full `https://` URLs.

## 4. Add code and datasets

Use `github` for an open-source repository:

```yaml
github: https://github.com/organization/repository
```

Use `miscs` for a dataset or other extra link. The `content_type` becomes the
link label shown on the publication page:

```yaml
miscs:
  - content_type: Dataset
    content_url: https://example.org/dataset
  - content_type: Supplementary Material
    content_url: /files/example-supplement.pdf
```

Do not use `osd` as a link. It is only descriptive text and does not create a
GitHub or Dataset button in the current publication layout.

## 5. Add the abstract

After the closing `---`, add the publication content. The abstract is normally
provided through the `description` field:

```yaml
description:
  - title: Abstract
    text: "Write the abstract here."
```

Do not add a second `Abstract` heading in the Markdown body. The publication
layout adds that heading automatically. Additional Markdown content can be
placed below the front matter when needed.

## 6. Check the result

Build or serve the site locally:

```bash
bundle exec jekyll serve
```

Open the publication list at `/publications/`, then open the new publication
and check its paper, code, dataset, image, and other links.

## Removing or updating a publication

Edit or delete the corresponding Markdown file in `_posts/`. Also remove any
unused PDFs from `/files` and cover images from `/assets/images/pubpic` after
confirming that no other page uses them.