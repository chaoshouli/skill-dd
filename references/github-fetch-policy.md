# GitHub Fetch Policy

Use this policy when the input is a GitHub repository URL.

## Default Route

Do not start with `git clone` for first-pass due diligence. For GitHub-hosted Skills and small repositories, use GitHub API first:

1. Read repository metadata:
   `https://api.github.com/repos/{owner}/{repo}`
2. Read the root contents tree:
   `https://api.github.com/repos/{owner}/{repo}/contents/`
3. Inspect only high-signal files and directories first:
   - `README.md`
   - `SKILL.md`
   - `references/`
   - `scripts/`
   - `examples/`
   - `agents/`
   - package or config files when present
4. Decode GitHub API `content` fields from base64 when needed.
5. Use `git clone` only when API evidence is insufficient, local script execution is required, full history matters, or binary/example assets must be inspected locally.

## Shell Notes

- Quote URLs containing `?ref=main` in zsh commands, otherwise `?` may be treated as a glob and fail with `no matches found`.
- For Node HTTPS calls to GitHub API, include a `User-Agent` header.
- If `raw.githubusercontent.com` or `git clone` is unstable, do not keep retrying. Fall back to API contents and state the evidence boundary.

## Evidence Boundary

When using API-only inspection, a first-pass report is valid if it covers metadata, `README.md`, `SKILL.md`, references, scripts, examples, and agent/config files. Lower confidence only when the repo's behavior depends on assets or scripts that were not inspected enough to validate.
