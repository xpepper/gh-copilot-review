
## 2024-04-18 - API Path Traversal in Repository Identifier
**Vulnerability:** The script extracted the repository identifier (`repo`) from the URL or git remote using basic string substitution or regex, and directly passed it to the `gh api` path `/repos/${repo}/...` without validation.
**Learning:** This could allow an attacker to inject path traversal sequences (like `..`) in the URL or local git remote to interact with unexpected endpoints on the GitHub API, assuming the caller has elevated privileges or executes the script on untrusted input.
**Prevention:** Always validate extracted variables before interpolating them into API paths or commands. Implement strict regex allowlisting for repository identifiers (e.g., `^[a-zA-Z0-9._-]+/[a-zA-Z0-9._-]+$`) and explicitly reject strings containing `..`.
