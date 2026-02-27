# OSTI — Security Audit TODO

Generated from security audit on 2026-02-26.

## High Priority

- [x] **Add a lockfile** — Generated `uv.lock` with `uv lock`. CI updated to install via `uv sync --frozen`. Also fixed stale package name (`linkml-schema-automator` → `schema-automator`).

## Medium Priority

- [x] **Pin GitHub Actions to SHA digests** — All actions in `release.yml` now use immutable SHA digests, including third-party `softprops/action-gh-release`.

- [x] **Add top-level workflow permissions default** — Added `permissions: contents: read` at workflow level in `release.yml`.

- [x] **Pin `hatch` version in CI** — Changed to `pip install hatch==1.16.4` in `release.yml`.

## Low Priority

- [x] **Remove committed `nul` file** — File was never tracked by git (already in `.gitignore`). No action needed.

- [x] **Add upper-bound version constraints** — `pydantic>=2.10,<3.0` in `pyproject.toml`.

- [x] **Pin `hatchling` build backend** — `hatchling>=1.21,<2.0` in `[build-system]` requires.

- [ ] **Add `--require-hashes` to CI pip installs** — Not applicable: CI now uses `uv sync --frozen` which verifies against `uv.lock` hashes natively.

## Informational / Hygiene

- [x] **Add key/cert patterns to `.gitignore`** — Added `*.pem`, `*.key`, `*.p12`, `*.pfx`.

- [ ] **Schema library design notes** — String fields (color, label, image_ref, Extension.url) have no length limits and coordinate fields lack `ge=0, le=100` range validators. This is acceptable for a library (consumers should enforce), but worth documenting in README or schema docs.

## Audit Summary

- **Code security (OWASP):** Clean — no vulnerabilities found
- **Secrets:** Clean — zero secrets in source or git history
- **Infrastructure:** N/A — no Docker/Terraform/K8s
- **Overall verdict:** Ready for deployment, no blocking issues
