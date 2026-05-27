# Developer Documentation

Welcome to the [Agent Finder](https://agentfinder-project.github.io/docs/) documentation repository. This guide covers local setup, the repository layout, deployment, and writing style.

> **Note:** This file is for contributors only. MkDocs excludes it from the published site because `index.md` is the public homepage.

---

## Repository layout

| Path | Purpose |
| :--- | :--- |
| `mkdocs.yml` | Site configuration, navigation, and theme |
| `docs/` | Published Markdown pages (MkDocs `docs_dir`) |
| `spec/agentfinder.md` | Canonical Agent Finder specification (included on the site via snippet) |
| `overrides/` | Material theme customizations |
| `.github/workflows/publish-docs.yaml` | Automated deploy to GitHub Pages on push to `main` |

The live site is published at **https://agentfinder-project.github.io/docs/**.

---

## 1. Getting started

You need Python 3.x and Git.

1. **Clone the repository**:
   ```bash
   git clone https://github.com/agentfinder-project/docs.git
   cd docs
   ```

2. **Create a virtual environment**:
   ```bash
   python3 -m venv .venv
   ```

3. **Activate the virtual environment** (optional):
   - Linux/macOS: `source .venv/bin/activate`
   - Windows: `.venv\Scripts\activate`

4. **Install dependencies**:
   ```bash
   .venv/bin/pip install -r requirements-docs.txt
   ```

---

## 2. Local development

Start the live-reload preview server from the repository root:

```bash
.venv/bin/mkdocs serve
```

- Open **http://127.0.0.1:8000/** in your browser.
- Edits under `docs/` rebuild automatically.
- Edits to `spec/agentfinder.md` also appear on the **Agent Finder Spec** page (`docs/spec.md` pulls that file in via a snippet).

To verify a production build locally:

```bash
.venv/bin/mkdocs build
```

---

## 3. Deployment

### Automated deployment (default)

Pushing or merging to `main` triggers the **Publish Docs** workflow (`.github/workflows/publish-docs.yaml`), which builds the site and deploys to the `gh-pages` branch on GitHub Pages.

No manual steps are required for routine doc updates merged to `main`.

### Manual deployment (optional)

If you have push access and need to deploy outside CI (for example, to test `gh-deploy` locally):

```bash
.venv/bin/mkdocs gh-deploy
```

This builds static assets, commits them to `gh-pages`, and pushes to GitHub.

---

## 4. Editing the specification

The full Agent Finder spec lives in **`spec/agentfinder.md`**. The site page `docs/spec.md` includes it with a snippet directive—edit the spec file directly rather than duplicating content in `docs/spec.md`.

---

## 5. Writing guidelines

Use an **anti-hype, high-density, clinical tone**:

- **Clear and concise:** State technical behavior directly. Avoid marketing superlatives (*"revolutionary"*, *"groundbreaking"*).
- **Grounded examples:** Use valid JSON with domain-anchored URNs (`urn:ai:<domain>:...`) and standard media types (for example `application/mcp-server+json`).
- **Spec alignment:** Terminology and schema examples should match `spec/agentfinder.md` and the [ai-catalog](https://github.com/Agent-Card/ai-catalog) standard.

---

## 6. Contributing

- **Spec and product discussion:** [agentfinder-project/agentfinder issues](https://github.com/agentfinder-project/agentfinder/issues)
- **Documentation changes:** Open a PR in this repository (`agentfinder-project/docs`). Public write access may be limited; ask in issues or [Discord](https://discord.gg/PK3DpEybzP) if you need collaborator access.

See also [Contributors](contributors.md) on the published site.
