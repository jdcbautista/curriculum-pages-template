# 1. Getting started

## Goals

By the end of this lesson you can:

- name the four files that make up this site
- explain why the site needs no build step

## How the site works

GitHub Pages serves the repository's files directly. `index.html` loads [docsify](https://docsify.js.org), which fetches the Markdown file named in the address bar and renders it in the browser.

| File | Job |
|------|-----|
| `index.html` | Site title, repository link and the docsify scripts |
| `home.md` | The landing page |
| `_sidebar.md` | The navigation on the left |
| `lessons/*.md` | One file per lesson |

The empty `.nojekyll` file tells GitHub Pages to serve files as they are, including those that start with an underscore such as `_sidebar.md`.

## Practice

1. Which file do you edit to change the site title?
2. Why does `_sidebar.md` need the `.nojekyll` file?

<details>
<summary>Answer key</summary>

1. `index.html`, the `name` setting.
2. Without it, GitHub Pages runs Jekyll, which hides files whose names start with `_`.

</details>
