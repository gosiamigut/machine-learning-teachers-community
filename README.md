# Machine Learning Teacher Community website

A Quarto website with four sidebar sections: **About us**, **Events**, **CAIT**, and **Micro-grant projects**. The micro-grant page shows all six projects one after another, each with a lead portrait on the left and description on the right. The layout stacks on small screens.

## Edit the website

| Section | File |
| --- | --- |
| About us (homepage) | `index.qmd` |
| Events | `events.qmd` |
| CAIT | `cait.qmd` |
| All six micro-grant projects | `micro-grant-projects.qmd` |
| Navigation and site settings | `_quarto.yml` |
| Styling | `styles.css` and `theme.scss` |

The first three pages contain starter text. Replace it with your community information, events, and CAIT details.

In `micro-grant-projects.qmd`, each project has its own numbered section. Edit its title, introductory sentence, lead name, affiliation, and description. Keep the layout markers (`:::`) intact. The six original portrait placeholders are in `assets/lead-01.svg` through `assets/lead-06.svg`.

For a real portrait, put the photo in `assets`, update the corresponding image path (for example to `assets/lead-01.jpg`), and change its `fig-alt` to `Portrait of [name]`. Project links can point directly to `micro-grant-projects.html#project-01` through `#project-06`.

Remove the template note at the bottom once the actual project information is ready.

Preview locally with `quarto preview`, or use **Quarto: Preview** in VS Code. R and Python are not required. Do not edit generated HTML in `_site`; the publishing workflow renders it automatically from these source files.

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

- `_quarto.yml`: website configuration and four navigation links.
- `index.qmd`, `events.qmd`, and `cait.qmd`: community pages.
- `micro-grant-projects.qmd`: all six projects, in order.
- `assets/`: six local portrait placeholders.
- `theme.scss` and `styles.css`: appearance and responsive layout.
- `.github/workflows/publish.yml`: automatic GitHub Pages publishing.
- `.nojekyll`: bypasses Jekyll processing.

Generated files in `_site` are not tracked; GitHub builds and deploys them.
