# Academic website of Md Amit Hasan Arovi

This repository contains the source for [amithasanarovi.github.io](https://amithasanarovi.github.io), an academic website built with Jekyll and GitHub Pages.

The site presents my research in concurrent and parallel computing, non-blocking data structures, and safe memory reclamation, along with my publications, teaching, software, talks, awards, and curriculum vitae.

## Main content files

- `_pages/about.md` — home page
- `_pages/research.md` — research overview and future directions
- `_pages/publications.md` — publication list and research links
- `_pages/teaching.html` — teaching experience and approach
- `_pages/projects.md` — research software and selected projects
- `_pages/talks.html` — conference presentations
- `_pages/awards.md` — awards and travel funding
- `_pages/cv.md` — CV download page
- `_config.yml` — site identity and profile links
- `_data/navigation.yml` — top navigation
- `_sass/_custom.scss` — custom visual design

## Preview locally on Linux

Install Ruby and Bundler, then run:

```bash
sudo apt update
sudo apt install ruby-dev ruby-bundler build-essential zlib1g-dev
bundle install
bundle exec jekyll serve
```

Open `http://localhost:4000` in a browser. Stop the server with `Ctrl+C`.

## Publish

GitHub Pages rebuilds the site after changes are pushed to the publishing branch. See [`PUBLISHING.md`](PUBLISHING.md) for the exact steps.

The underlying theme is based on [Academic Pages](https://academicpages.github.io/) and [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/).
