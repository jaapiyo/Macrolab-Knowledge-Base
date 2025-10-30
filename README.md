# Knowledge Base — MkDocs quick start

This short guide helps new contributors get MkDocs running locally so you can preview edits, build the static site, and understand how CI deploys to the `gh-pages` branch or your server.

## What you'll get

- A local dev server with live reload for files under `docs/`.
- Commands to build the static site into `site/` and to publish (GitHub Pages or upload to a server).
- A recommended contribution workflow (branch → PR).

## Prerequisites

- Python 3.8+ on your PATH
- Git
- A GitHub account (to open pull requests)

## Quick setup (PowerShell)

1. Clone the repo and enter it:

```powershell
git clone https://github.com/jaapiyo/Knowledge-Base.git
cd "Knowledge-Base"
```

2. Create and activate a virtual environment:

```powershell
python -m venv .venv
# If PowerShell blocks activation, run once in the shell:
# Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\.venv\Scripts\Activate.ps1
```

3. Install MkDocs + plugins used in this repo:

```powershell
pip install --upgrade pip
pip install mkdocs mkdocs-material mkdocs-git-revision-date-localized-plugin mkdocs-git-authors-plugin mkdocs-awesome-nav
```

Tip: add a `requirements.txt` with the packages above and contributors can run `pip install -r requirements.txt`.

## Run the dev server

```powershell
mkdocs serve -a 0.0.0.0:8000
```

Open http://127.0.0.1:8000 in your browser. Edits under `docs/` will auto-reload.

## Build the static site

```powershell
mkdocs build
# Output is placed into the `site/` folder
```

## Publish

- GitHub Pages (recommended / used by CI):

```powershell
mkdocs gh-deploy --force
```

This generates the site and pushes to the `gh-pages` branch.

- Deploy to your own server (FTP/SFTP):

1. `mkdocs build` to create `site/`
2. Mirror the contents of `site/` to your server using your FTP/SFTP client or an automated script.

Note: This repository's CI (`.github/workflows/ci.yml`) already runs `mkdocs gh-deploy` and then checks out `gh-pages` to upload via SFTP (requires repository secrets like `FTP_HOST`, `FTP_USERNAME`, `FTP_PASSWORD`).

## Contributing workflow (recommended)

1. Create a branch for your changes:

```powershell
git checkout -b fix/docs-typo
```

2. Edit or add Markdown files under `docs/`.
3. Preview with `mkdocs serve` locally.
4. Commit, push the branch, and open a PR for review.

## Troubleshooting & common issues

- Activation blocked by PowerShell ExecutionPolicy:
	- `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass`
- Python/pip not found:
	- Confirm with `python --version` and `pip --version` and ensure Python was added to PATH.
- MkDocs errors about missing plugins:
	- Install required plugins and restart the dev server.
- `mkdocs gh-deploy` fails due to permissions:
	- Make sure your Git remote is correct and you have push access.

## Helpful additions (recommended)

- `requirements.txt` that lists the MkDocs theme and plugins so contributors can install dependencies with one command.

Example `requirements.txt`:

```
mkdocs
mkdocs-material
mkdocs-git-revision-date-localized-plugin
mkdocs-git-authors-plugin
mkdocs-awesome-nav
```

- Add a short `CONTRIBUTING.md` with the steps above and any repo-specific guidance (PR labels, branch naming, review expectations).

## Try it — copyable snippet

```powershell
git clone https://github.com/jaapiyo/Knowledge-Base.git
cd "Knowledge-Base"
python -m venv .venv
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt   # or install packages listed above
mkdocs serve
```