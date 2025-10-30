# Contributing to Knowledge Base

Thanks for helping improve this knowledge base — your contributions are welcome.

## Quick start (local)

1. Fork the repository and clone your fork:

```powershell
git clone https://github.com/<your-username>/Knowledge-Base.git
cd "Knowledge-Base"
```

2. Create and activate a virtual environment (PowerShell):

```powershell
python -m venv .venv
# If PowerShell blocks activation:
# Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\.venv\Scripts\Activate.ps1
```

3. Install dependencies:

```powershell
pip install --upgrade pip
pip install -r requirements.txt
```

4. Run the local preview server:

```powershell
mkdocs serve
```

Open http://127.0.0.1:8000 and confirm your changes render as expected.

## Branching & PRs

- Create a short-lived feature branch for your change:

```powershell
git checkout -b feat/short-description
```

- Make small, focused commits with meaningful commit messages.
- Push the branch and open a pull request against `jaapiyo/Knowledge-Base:main`.
- Link any relevant issue(s) and add a short description of the change.

## Content guidelines

- Add pages or edit Markdown files under `docs/`.
- Keep page content focused and use existing style / tone.
- Use relative links for internal docs (e.g., `../control-systems/index.md`).
- Prefer concise headings and short paragraphs. Where helpful, add images under `media/` and reference them with relative paths.

## Preview & checks

- Always preview changes locally with `mkdocs serve` before opening a PR.
- CI will run the build and (if configured) deploy the generated site.

## Deploys and CI

- This repository's CI builds with `mkdocs gh-deploy` and then uploads the `gh-pages` branch to a server via SFTP. The deploy step requires the repository to have secrets such as `FTP_HOST`, `FTP_USERNAME`, and `FTP_PASSWORD` configured by repository maintainers.
- As a contributor, you generally only need to open a PR — maintainers will handle deploy secrets and final publishing.

## Troubleshooting

- If activation fails, run: `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass` in PowerShell, then re-run the Activate script.
- If a plugin is missing, install it (`pip install <plugin>`) and restart the dev server.

## Style & formatting

- Use plain Markdown. Keep code examples fenced and language-tagged (e.g., ```powershell).
- If you change navigation or site-wide config, note it in the PR description so reviewers can check `mkdocs.yml` changes.

## Thank you

Thanks for contributing — small edits and clarifications help a lot. If you're unsure about a large structural change, open an issue first to discuss.
