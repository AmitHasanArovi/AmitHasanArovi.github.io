# Publishing the website

The website is ready to publish at `https://amithasanarovi.github.io`.

## 1. Review the updated files

Before publishing, confirm that these details are current:

- personal email in `_config.yml`
- current appointment and course list in `_pages/about.md` and `_pages/teaching.html`
- publication links in `_pages/publications.md`
- the PDF at `files/CV_MdAmitHasanArovi.pdf`

## 2. Commit and push

From the repository folder, run:

```bash
git status
git add -A
git commit -m "Update academic website"
git push origin master
```

If the repository uses `main` instead of `master`, replace the final command with:

```bash
git push origin main
```

## 3. Check GitHub Pages

In the GitHub repository, open **Settings → Pages**. Under **Build and deployment**, use **Deploy from a branch** and select the branch you pushed, with the folder set to `/ (root)`.

GitHub normally publishes the update within a few minutes. Then open:

`https://amithasanarovi.github.io`

Check the home page, mobile navigation, publication links, profile links, and CV download.

## Updating later

- Replace `files/CV_MdAmitHasanArovi.pdf` whenever the CV changes; keep the filename unchanged so existing links continue to work.
- Add publications to `_pages/publications.md` and selected highlights to `_pages/about.md`.
- Update the current appointment and courses in `_pages/about.md` and `_pages/teaching.html`.
