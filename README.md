# WAYS Lab Website

This is a [Jekyll](https://jekyllrb.com/) static site hosted on GitHub Pages. Below are instructions for running it locally and for modifying its content.

## Table of Contents

- [Getting Started with Website](#getting-started-with-website)
  - [Recommended: Docker](#recommended-docker)
  - [Verifying your changes work](#verifying-your-changes-work)
  - [Native Ruby alternative (no Docker)](#native-ruby-alternative-no-docker)
  - [Deploying changes](#deploying-changes)
  - [Cleanup / troubleshooting](#cleanup--troubleshooting)
  - [Quick Reference](#quick-reference)
- [How to modify some things](#how-to-modify-some-things)
  - [Home Page](#home-page)
  - [Team Page](#team-page)
  - [Research Pages](#research-pages)
  - [Publications](#publications)
  - [Website Extensions / TODOs](#website-extensions--todos)
- [File Structure](#file-structure)
- [More Information](#more-information)

---

## Getting Started with Website

The maintainers' recommended workflow uses **Docker Compose**, with a native Ruby fallback. The setup works on Windows, Linux, and Mac (Intel and Apple Silicon).

**Prerequisites**
- **Docker Desktop**: [Download & install](https://www.docker.com/products/docker-desktop/) (Mac, Windows, or Linux).
- **Docker Compose**: Included with Docker Desktop (use `docker compose`, not `docker-compose`).

### Recommended: Docker

```bash
# 1. Fresh clone
git clone git@github.com:wayslab/wayslab.github.io.git
cd wayslab.github.io

# 2. Build the image (only needed once, or after Dockerfile/Gemfile changes)
docker compose build

# 3. Edit whatever you want to change:
#    - Content pages: index.md, about.md, team.md, vacancies.md, etc. (Markdown)
#    - Site config:   _config.yml
#    - Layout/HTML:   _layouts/, _includes/
#    - Styles:        _sass/
#    - Data:          _data/
#    - Assets/images: assets/, files/

# 4. Start the live-reload dev server
docker compose up local
```

Then open **http://localhost:4000** (equivalently http://0.0.0.0:4000). The `local` service runs `jekyll serve --watch --force_polling`, so saving a `.md`, `_config.yml`, or `_sass` file rebuilds automatically — just refresh the browser. To stop the server, press **Ctrl+C**.

> **Note:** `--force_polling` means a `_config.yml` change *does* get picked up here (normally Jekyll ignores config changes without a restart), but to be safe, `Ctrl+C` and re-run `docker compose up local` after editing `_config.yml`.

### Verifying your changes work

1. **Live preview** — with `docker compose up local` running, browse to `http://localhost:4000` and click through the pages you edited. Watch the terminal: Jekyll prints a rebuild line on each save, and any Liquid/YAML error shows up there (the page will 500 or fail to build if broken).
2. **Production-parity build** — before pushing, confirm it builds clean the way GitHub Pages will:
   ```bash
   docker compose run --rm remote      # runs JEKYLL_ENV=production jekyll build
   ```
   Output lands in `_site/`. If this exits 0 with no errors, your change is safe to push.
3. **Optional lint** (if you touched JS/SCSS): `npm run eslint` / `npm run stylelint`.

### Native Ruby alternative (no Docker)

The repo targets Ruby 3.3 (see `Dockerfile`) with Bundler 2.4.22. Docker generally works much better, but native works too:

```bash
git clone git@github.com:wayslab/wayslab.github.io.git
cd wayslab.github.io
gem install bundler -v 2.4.22
bundle install
bundle exec jekyll serve -H 0.0.0.0        # → http://localhost:4000
```

Production check: `JEKYLL_ENV=production bundle exec jekyll build` (or `npm run build`).

### Deploying changes

Two ways to deploy the built site:

1. **(Recommended)** Simply commit the changes on GitHub and push the changes in your GitHub branch. The owner can push directly to the `master` branch; others can open a merge request. Once the code is merged into `master`, GitHub automatically runs the rsync automation to update the live website. Track and debug it via the **Actions** tab on the GitHub project. Issue with the GitHub automation running on the wcsng-18 machine? Contact Gavin or Vatsank.
2. **(Manual — not recommended, but works for urgent needs)** Directly rsync the `_site/` directory to the server.

### Cleanup / troubleshooting

- Stale output or weird caching: `docker compose run --rm cleanup` (removes `_site/` and sass cache).
- **Gemfile changes?** Rebuild the image: `docker compose build`.
- **Port 4000 already in use?** Stop other containers, or remap in `docker-compose.yml` (e.g. `"8080:4000"` → browse `http://localhost:8080`).

Two things worth flagging about this specific repo:
- `_config.yml` has **empty `url` and `baseurl`**, so links resolve correctly at `localhost:4000` root — no path prefix to worry about locally.
- The active branch is `master` (that's `origin/HEAD`), so a fresh clone lands you on the right branch by default.

### Quick Reference

| Command                             | Purpose                        |
|-------------------------------------|--------------------------------|
| `docker compose build`              | Build the Docker image(s)      |
| `docker compose up local`           | Launch live dev site (4000)    |
| `docker compose run --rm remote`    | Run production site build      |
| `docker compose run --rm cleanup`   | Remove `_site/`, clean cache   |

---

## How to modify some things

### Home Page

To update the images in the carousel, go to `index.md` and update the image paths under the carousels in the front matter.
To change the research areas or their overview gifs, update the corresponding heading, link, and path in the body of `index.md`.
For now, these research areas are hardcoded, but it could be automated if they change a lot by creating a `.yml` file.

### Team Page

To update current PhD students, Postdocs, or Collaborators, add (or remove) an entry in `/_data/people.yml`. Be sure to follow the same format as the existing entries with name, role, and a path to their image. These images should be saved to `/assets/images/teampic`.
To update current Masters and Undergraduate students, add (or remove) an entry in `/_data/people_text.yml`. Again, be sure to follow the same format as the existing entries. For the `col` field, alternate 1 and 2 for each additional entry to make sure that the names are evenly split across both columns.
To update Alumni, add (or remove) an entry in `/_data/alumni.yml`. Be sure to alternate the col values for each entry, as described above. For the `role` field, put the degree for all alumni (BS, MS, PhD etc.). For the `year` field, put the graduating year for all alumni. The `now` field can be left empty if unknown, or phrased " [company] [location]" or "[degree] at [school]".

### Research Pages

To add a new research page, create a new md file in the [ucsdwcsng/site-research-pages](https://github.com/ucsdwcsng/site-research-pages) submodule and put `layout: research` in the front matter. Add `permalink` field to be the same as the filename. Add the `pubtag` field to indicate which publications to display on the list of that research page. Be sure to match the spelling exactly to the corresponding tag on the publications. The `heading` field should have the title of the research page (it is not `title` for this layout since we want to display it below the research navbar). The `people` field is a list of the phd and postdoc students involved in this research area. Add them in the following format, and the layout will automatically pull their images from the people.yml file:
```
people:
  - Dinesh Bharadia
  - Roshan Ayyalasomayajula
  - Ish Kumar Jain
  - Aditya Arun
  - Wei Sun
  - Deepak Vasisht
  - Shunsuke Saruwatari
  - Chi Zhang
```
The `sponsors` field is optional, and should include a list of sponsors and their logos in the following format:
```
sponsors:
  - name: Qualcomm
    picture: /assets/images/qualcomm.jpeg
```
Finally, use the `carousels` field to add the research page's carousel images using the following format:
```
carousels:
  - images:
    - image: /assets/images/atkinson.jpeg
    - image: /assets/images/rice_chip.jpeg
    - image: /assets/images/pcb.jpeg
    - image: /assets/images/bearl.jpeg
```
To update the site navigation, add/change an entry to `subfolderitems` in `_data/navigation.yml`.

### Publications

To add a new publication (both to the publications list and as an individual webpage), create a new md file under the [ucsdwcsng/site-publications-pages](https://github.com/ucsdwcsng/site-publications-pages) submodule. Be sure to name the md file with the format `year-month-day-name.md` (ex: 2023-05-24-mmSpoof.md). In the front matter of this md file, add `layout: publication`. The `title` field should have the full name of the publication, which will be displayed as the title of the publication's webpage. The `short_title` field is the shortened name that will be displayed on the list views of the publication. The `tags` field is a space separated list to tag which sublists and research pages this publication should appear in. Be very careful to match the spelling exactly to existing tags, or it will create a new tag for this publication. The `cover` field should have the path to the cover image to be displayed on the publication list. All cover images should be saved to /assets/images/pubpic. The `authors` field should be a string of authors separated by commas (try to write full names and only commas, no "and" to maintain consistency). The `conference` field stores the name of the conference this paper was used in. The `paper` field is required, and should contain a link or path to a pdf of the paper. Most of these pdfs are stored in /files. The optional fields are `github`, which should have a link to the github repo, `dataset`, which should have a link the the dataset, `slides`, which should have a path to a pdf of the slides (most are saved in /files), `extra`, which should have a string about the special highlight of this publication (ex: `extra: "This work won the Qualcomm Innovation Fellowship 2022!"`), and `video`, which should have an EMBED link to a youtube video (not the regular youtube link). Currently, up to two video links are automatically supported, with the field for the second video being `video2` (which will also require a youtube embed link). Up to one additional link is also supported under the field `other`, which will show up in the list of links containing the slides, github, and datasets. The format for adding this extra link is:
```
other:
  display: "[Kaggle Competition]"
  url: https://www.kaggle.com/competitions/wildv2/data
```
Another optional field is `press` to show any press coverage. Currently, upto 4 press links are supported (with fields `press`, `press2`, `press3`, and `press4`), and the format to add them is as follows:
```
press:
  date: "November 20, 2020"
  url: https://www.10news.com/news/local-news/uc-san-diego-researchers-find-ways-to-make-self-driving-cars-safer
  headline: UC San Diego Researchers Find Ways to Make Self-Driving cars Safer
```
The `osd` field (named osd as short for Open Source Description - feel free to rename if you can think of a better option) is optional, and should contain a string with a short description of the publication's associated code and/or dataset to be displayed on the Open Source page.
The last optional front matter field is the `highlight` field. This field is a boolean used to determine whether this publication should be one the publications displayed on the shortened list of its corresponding research page. If `highlight` is `true`, then the publication will appear on the shortened research page list. If it is `false`, or the `highlight` field is missing, then it won't.
Finally, the Abstract should be added to the body of the md file. Don't add a heading for the abstract, since that formatting is already automated by the publication layout. Any customized headings, images, and videos can also be added in the body, and will be displayed below the abstract on the webpage.
The publication list will display icon links for any provided github, slides, and paper, but not any of the other optional fields. The other optional fields will be viewable on the publications webpage, which will be accessible by clicking the title on the publications list, or the shortened list on any of the research pages.

### Website Extensions / TODOs

- **Home Page** — Currently, the home page layout is quite concrete, but it is missing content. The images in particular have to be updated. The banner image at the top of the page should be discussed and carefully chosen. For each of the research sections, we have discussed adding high quality short gifs in place of the current images. These have to be created and updated as well.
- **Team Page** — The layout of this page is close to done, but the lists need to be updated. Many of the people displayed as current students have graduated, and many new students have joined the lab. This information needs to be updated in the `.yml` files mentioned earlier to make a more current list. We have also discussed the idea of hiding the alumni list and having a 'show more' button to display it, since the length of the list makes the page feel cluttered. There is no code to support this feature yet, and the layout of the team page would have to be updated to support it.
- **Research** — Make the "show more" link in the shortened publications list lead to the filtered main publications list (instead of unfiltered). Also expand the code and datasets section with more information or images.
- **Publications** — Add a second set of tags for the technology used in each publication. Distinguish it with a separate colour, or have a filter to switch between application tags and technology tags.

---

## File Structure

```text
/
├── Dockerfile
├── docker-compose.yml
├── Gemfile
├── _config.yml
├── index.md, about.md, team.md, ...   # content pages (Markdown)
├── _data/                             # people, navigation, alumni (YAML)
├── _layouts/, _includes/             # page templates & partials
├── _sass/                            # styles
├── assets/, files/                   # images & downloadable files
└── _site/                            # (generated after build)
```

## More Information

- [Jekyll Docs](https://jekyllrb.com/docs/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Docker Compose](https://docs.docker.com/compose/)
