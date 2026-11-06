# Quarto project showcase

A six-project website with a persistent left sidebar. Each project opens with a portrait of its lead on the left and a description on the right. On phones, the portrait appears above the description and Quarto provides a collapsible navigation menu.

All project names, portraits, and text are clearly marked placeholders. No real people or projects are represented.

## Start here

1. Unzip this folder.
2. Open the folder in VS Code. If using the Quarto extension, choose **Quarto: Preview** from the Command Palette while a `.qmd` file is open. Alternatively, run `quarto preview` in this folder.
3. Replace the placeholder content using the table below.
4. Publish using the GitHub Pages instructions below.

Quarto is needed for local preview; R and Python are not required by this website. The publishing workflow installs Quarto automatically on GitHub.

## Edit your projects

| Project | Page to edit | Portrait placeholder |
| --- | --- | --- |
| 01 (homepage) | `index.qmd` | `assets/lead-01.svg` |
| 02 | `project-02.qmd` | `assets/lead-02.svg` |
| 03 | `project-03.qmd` | `assets/lead-03.svg` |
| 04 | `project-04.qmd` | `assets/lead-04.svg` |
| 05 | `project-05.qmd` | `assets/lead-05.svg` |
| 06 | `project-06.qmd` | `assets/lead-06.svg` |

For each `.qmd` file:

1. Change `title:` at the top. The sidebar label and large page heading both use this title automatically.
2. Update `description:` at the top: this is the page's search-engine description.
3. Replace the introductory sentence, lead's name, affiliation, and main description.
4. Put the real photo in `assets`, for example `assets/lead-01.jpg`. Change the image line from `.svg` to `.jpg`, and change `fig-alt` to `Portrait of [name]`. Portrait photos work best; CSS crops them consistently.
5. Remove the entire `.template-note` block when the page is ready. Keep the `:::` layout markers around other sections.
6. Update the visible names in the previous/next links near the bottom if you want them to match your new titles. Keep their `.qmd` link targets unchanged, or delete the whole `.project-pagination` block.

Use Markdown for links, for example `[Read the paper](https://example.org/paper)` or `[Contact the lead](mailto:name@example.org)`.

The headings and bullets in the description are optional. Replace them with plain paragraphs if you prefer.

To change the site name, edit `website.title` and `website.page-footer.left` in `_quarto.yml`. Update the sidebar and page footers as desired. Colours and typography are in `theme.scss`; layout details are in `styles.css`.

## Publish on GitHub Pages — automatic updates

These instructions are for a **new, separate repository**, such as `project-showcase`. They do not modify an existing personal website.

1. Create an empty repository on GitHub. A public repository works with GitHub Free. Give it a name such as `project-showcase`; choose `main` as the default branch.
2. Put **the contents of this folder** at the repository root, with `_quarto.yml` directly at the root. Include `.github/workflows/publish.yml`, `.gitignore`, and `.nojekyll`. Do not upload the ZIP itself, the containing folder, or the generated `_site` directory.
3. In the repository, open **Settings → Pages**. Under **Build and deployment → Source**, choose **GitHub Actions**.
4. Open **Actions → Publish Quarto website to GitHub Pages → Run workflow** and run it for `main`. Later pushes to `main` publish automatically.
5. Wait for the workflow to finish successfully. Its deployment link and **Settings → Pages** show the published address, normally `https://YOUR-USERNAME.github.io/project-showcase/`.

The workflow builds Quarto and deploys `_site` through GitHub's Pages actions. No personal access token or `_publish.yml` file is needed for this setup. GitHub supplies its workflow token.

**Uploading on a Mac:** folders beginning with a dot may be hidden in Finder. Press **Command–Shift–.** to show them. Make sure `.github/workflows/publish.yml` reaches GitHub: without it, automatic publishing will not run. If necessary, create it in GitHub with **Add file → Create new file**, enter `.github/workflows/publish.yml` as its full name, and paste the supplied workflow.

### Optional: publish with Git from Terminal

Run these commands inside the unzipped `project-showcase` folder after creating the empty GitHub repository. Replace the example remote URL with your own.

```bash
git init -b main
git add .
git commit -m "Add Quarto project website"
git remote add origin https://github.com/YOUR-USERNAME/project-showcase.git
git push -u origin main
```

Then complete steps 3–5 above. GitHub may ask you to authenticate.

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

- `_quarto.yml`: website settings and six-project navigation.
- Six `.qmd` files: project content, with project 01 as the homepage.
- `assets/`: six original SVG placeholders, ready to replace with photos.
- `theme.scss` and `styles.css`: appearance and responsive layout.
- `.github/workflows/publish.yml`: automatic GitHub Pages publishing.
- `.nojekyll`: bypasses Jekyll processing.
- `_site/`: a rendered copy for inspection, included in this ZIP but ignored by Git.

There are no analytics, external fonts, or third-party photo requests.

## Documentation

- [Quarto website navigation](https://quarto.org/docs/websites/website-navigation.html)
- [Quarto and GitHub Pages](https://quarto.org/docs/publishing/github-pages.html)
- [GitHub Pages custom workflows](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages)
- [Install Quarto](https://quarto.org/docs/get-started/)

## Validation

Rendered successfully with Quarto 1.11.9. All six pages were checked for navigation targets, active-page states, portrait and description elements, and local assets. The desktop layout and mobile navigation were checked in a browser. The GitHub Actions workflow is included and its configuration was checked, but it has not been run in your GitHub account.
