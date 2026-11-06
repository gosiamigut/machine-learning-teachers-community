# Machine Learning Teacher Community website

A Quarto website with six sidebar sections, in order: **Events**, **CAIT**, **Research & Innovation**, **Micro-grant projects**, **Community blog**, and **About us**. Events is the landing page. The micro-grant page shows all six projects one after another, each with a lead portrait on the left and description on the right. The layout stacks on small screens.

## Edit the website

| Section | File |
| --- | --- |
| Events (homepage) | `index.qmd` |
| CAIT | `cait.qmd` |
| Research & Innovation | `research-innovation.qmd` |
| All six micro-grant projects | `micro-grant-projects.qmd` |
| Community blog | `community-blog.qmd` |
| About us | `about.qmd` |
| Navigation and site settings | `_quarto.yml` |
| Styling | `styles.css` and `theme.scss` |

The community pages contain information adapted from TU Delft and public LinkedIn updates. `CONTENT_SOURCES.md` records the sources and remaining gaps. The previous `events.html` address redirects to the Events homepage.

Edit sponsors in `website.page-footer` in `_quarto.yml`; the footer appears on every page. The current sponsors are TU Delft and AI Initiative. For events, update the featured gathering and move it into the year archive after it has taken place.

In `micro-grant-projects.qmd`, five project descriptions and their teams are filled from the supplied document. The sixth section is reserved for the remaining project. Keep the layout markers (`:::`) intact when editing. The open-book project uses a small portrait grid for its five applicants.

For a real portrait, put the photo in `assets`, update the corresponding image path (for example to `assets/lead-01.jpg`), and change its `fig-alt` to `Portrait of [name]`. Project links can point directly to `micro-grant-projects.html#project-01` through `#project-06`.

Replace the “More to come” section once the sixth project is available. The DigiPedia abstract in the supplied document was incomplete; add its final part when supplied.

Preview locally with `quarto preview`, or use **Quarto: Preview** in VS Code. R and Python are not required. Do not edit generated HTML in `_site`; the publishing workflow renders it automatically from these source files.

## Publish on GitHub Pages — automatic updates

This site is published at <https://gosiamigut.github.io/machine-learning-teachers-community/> from the `main` branch of `gosiamigut/machine-learning-teachers-community`.

Saving changes to `main` automatically runs **Publish Quarto website to GitHub Pages**. To run it manually, open **Actions**, select that workflow, then choose **Run workflow → main**. In **Settings → Pages**, the source must remain **GitHub Actions**.

The workflow installs Quarto, renders the source files, and deploys `_site`. No personal access token or `_publish.yml` is needed. Keep `.github/workflows/publish.yml` in the repository.

### Updating the published website

Edit the `.qmd` files and photos, then commit your changes to `main`. GitHub will rebuild and publish the site. You can edit text directly on GitHub using its file editor, or work locally in VS Code and push your changes.

### If publishing fails

- Confirm **Settings → Pages → Source** is **GitHub Actions**.
- Confirm the repository default branch is `main`. If you use another branch name, update `branches: [main]` in the workflow and any environment restrictions.
- Confirm `.github/workflows/publish.yml` is present and Actions are enabled for the repository.
- Inspect the failed step in the Actions log; an organisation may restrict which third-party actions are allowed.

## Local commands

```bash
quarto preview
quarto render
```

`quarto render` generates the static website in `_site`. Edit the source files rather than the generated HTML. Internal links are relative, so the site can work at a repository subpath or a domain root.

## Included files

- `_quarto.yml`: website configuration and six navigation links.
- `index.qmd`: Events homepage.
- `cait.qmd`, `research-innovation.qmd`, `community-blog.qmd`, and `about.qmd`: community pages.
- `micro-grant-projects.qmd`: all six projects, in order.
- `assets/`: project portraits, original portrait placeholders, and community photographs.
- `CONTENT_SOURCES.md`: content provenance and outstanding details.
- `theme.scss` and `styles.css`: appearance and responsive layout.
- `.github/workflows/publish.yml`: automatic GitHub Pages publishing.
- `.nojekyll`: bypasses Jekyll processing.

Generated files in `_site` are not tracked; GitHub builds and deploys them.

### Colours, typography, and sponsor marks

Edit `theme.scss` for Quarto theme settings and `styles.css` for the page layouts.
The shared footer is in `_quarto.yml`. Keep sponsor marks in `assets/brand/`
unchanged; their official sources are recorded alongside them. Roboto Slab is
served locally from `assets/fonts/`; retain its Apache 2.0 license if redistributing.

Events remains the landing page. The sidebar keeps About us at the bottom on
desktop. Project jump links use the existing `#project-01` through `#project-06`
anchors. Mobile navigation uses Quarto's built-in menu.
