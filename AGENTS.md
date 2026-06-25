# AGENTS.md

Guidance for AI agents working in this repository.

## Project overview

**meronsolutions-login** is a minimal static site: one HTML page (`meronsolutionspoc.html`) and a logo image (`MeronSolutions_POC_Logo.png`). There is no application server, package manager, build step, database, or test suite in the repo.

## Cursor Cloud specific instructions

### Services

| Service | Required | Notes |
|---------|----------|--------|
| Static HTTP server | Yes (for E2E / browser testing) | Serves files from the repo root. Do **not** rely on `file://` for verification—the logo uses a relative path and is best tested over HTTP. |

There are no other local services (API, DB, Docker Compose, etc.).

### Run the site (development)

From the repository root:

```bash
python3 -m http.server 8080
```

Then open: `http://127.0.0.1:8080/meronsolutionspoc.html`

Alternative (Node available on the VM but not required by the repo):

```bash
npx --yes serve -l 3000
```

Use a **tmux** session for long-running servers so they survive across agent steps (see Cloud Agent shell conventions).

### Lint / test / build

- **Lint:** Not configured (no ESLint, HTML validator, or CI in repo).
- **Tests:** None.
- **Build:** None—edit HTML/assets directly; no bundler.

Smoke verification after changes: HTTP 200 for both `meronsolutionspoc.html` and `MeronSolutions_POC_Logo.png`, and visual check of title, blue layout, logo, and `mailto:support@meronsolutions.com` link.

### Secrets and environment variables

None required for local development of this repository.

### Salesforce / login

Copy on the page references a “secure Salesforce testing environment,” but **this repo does not implement Salesforce or login**. Any real SSO/Salesforce work would be in other systems, not here.
