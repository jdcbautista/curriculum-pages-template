# Curriculum Pages Template

A reusable GitHub template for curriculum websites written only in Markdown. GitHub Pages serves the files directly, so there is **no build step, no dependencies and no CI** to maintain.

- Live template: https://jdcbautista.github.io/curriculum-pages-template/
- Example built from it: https://jdcbautista.github.io/spanish-a1-curriculum/ (Spanish for beginners)
- Owner: the Curriculum Pipeline (JC Labs). The pipeline lists every site made from this template in its `repositories.json`.

## Files

| File | What it is | Edit it when |
|------|------------|--------------|
| `index.html` | Site settings (title, repo link) and the pinned [docsify](https://docsify.js.org) scripts | Renaming the site or upgrading docsify |
| `home.md` | Landing page and course outline | The course description or outline changes |
| `_sidebar.md` | Navigation, in lesson order | You add, remove or reorder a lesson |
| `lessons/NN-topic.md` | One lesson per file | Writing content |
| `.nojekyll` | Empty file; makes Pages serve `_sidebar.md` | Never — do not delete it |
| `VERSION`, `CHANGELOG.md` | The site's version and its history | Every published change |

## Build: start a new curriculum

**In the browser:** open this repository on GitHub → **Use this template** → **Create a new repository** → make it **Public**. Then in the new repo: **Settings → Pages → Build and deployment → Deploy from a branch → `main` / `/ (root)` → Save**.

**From a terminal** (GitHub CLI), replacing `spanish-a1-curriculum` with your repo name:

```bash
gh repo create spanish-a1-curriculum --public --clone --template jdcbautista/curriculum-pages-template
```

```bash
cd spanish-a1-curriculum && gh api -X POST "repos/{owner}/{repo}/pages" -f "source[branch]=main" -f "source[path]=/"
```

The site appears at `https://<your-user>.github.io/<repo-name>/` about a minute later.

Then make it yours:

1. In `index.html`, change `name` and `repo`.
2. Replace `home.md` with your course description and outline.
3. Replace the files in `lessons/` and list them in `_sidebar.md`.
4. Set `VERSION` to `0.1.0` and start `CHANGELOG.md`.

> GitHub Pages on a free account needs a **public** repository. Private repositories need a paid plan.

## Run: preview locally

Any static file server works. With Python (already on macOS):

```bash
python3 -m http.server 8000
```

Open http://localhost:8000. Refresh the browser after editing a Markdown file; there is nothing to rebuild.

## Maintain

**Add a lesson**

1. Create `lessons/NN-topic.md` using the format in [Writing a lesson](lessons/02-writing-a-lesson.md): Goals, teaching sections, Practice, then a collapsible Answer key.
2. Add it to `_sidebar.md` and to the outline table in `home.md`.
3. Preview locally, then commit and push. Pages republishes in about a minute.

**Rename or move a lesson:** rename the file, then update its links in `_sidebar.md`, `home.md` and any lesson that links to it. Search the repo for the old filename before committing.

**Version every change:** bump `VERSION` (patch for fixes, minor for new lessons), add a `CHANGELOG.md` line, and commit with the version in the message, e.g. `v0.2.0: add lesson 5`.

**Upgrade docsify:** the scripts in `index.html` are pinned to an exact version (`docsify@4.13.1`). To upgrade, change the version in all three URLs, preview locally, and check search and Previous / Next still work.

**Check the live site:** **Settings → Pages** shows the URL and the last deployment. The repository's **Actions** tab lists each `pages build and deployment` run; a red run names the file that failed.

**Troubleshooting**

| Symptom | Fix |
|---------|-----|
| Sidebar missing on the live site | `.nojekyll` was deleted; restore the empty file |
| A page shows "404 - Not found" | The link path or filename is wrong; paths are relative to the repo root and case-sensitive |
| Answer key shows raw Markdown | Add a blank line after `<summary>…</summary>` and before `</details>` |
| Site shows "Loading…" forever | The docsify CDN URL in `index.html` is wrong or blocked; check the browser console |

## Pull template improvements into an existing course

Sites made from a template do not share history with it. To take a template fix, copy the changed file (usually `index.html` or `.nojekyll`) and keep your own `name` and `repo` settings.
