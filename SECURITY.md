# Security Policy

## Supported Versions

Artifact Vault is a single-file app with no release cadence yet — only the latest code on `main` is supported.

## Reporting a Vulnerability

**Do not open a public issue for security problems.**

Use private vulnerability reporting instead: open the repo's **Security** tab and click **"Report a vulnerability"**. The report goes privately to the maintainer.

You'll get an acknowledgment within a few days. Fixes ship as commits to `main` and are noted in the [changelog](CHANGELOG.md). Coordinated disclosure (staying private until a fix is out) is preferred.

## Scope

Artifact Vault's security model:

- Read-only local file access via the File System Access API (`read` mode)
- Previews run in sandboxed iframes with scripts disabled
- The app itself makes no network requests (libraries are vendored inline)

Reports of sandbox escape, unexpected write/delete access to your files, data leaving the machine, or malicious-file rendering escapes are especially relevant.

Out of scope:

- Content rendered *inside* previews loading external images/CSS — this is documented behavior (see README → Privacy & Security)
- Vulnerabilities in the vendored libraries themselves — report those upstream to [marked](https://github.com/markedjs/marked) or [highlight.js](https://github.com/highlightjs/highlight.js)
