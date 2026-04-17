## 2024-05-24 - API Path Traversal
**Vulnerability:** Path traversal in `gh api` calls through unvalidated `$repo` values.
**Learning:** URL-based parameters extracted from user inputs must be explicitly validated before being used in paths, even if they pass regex validation that's designed to loosely extract components.
**Prevention:** Always use regex matching for a strict whitelist of allowed formats (`^[a-zA-Z0-9._-]+/[a-zA-Z0-9._-]+$`) and perform explicit string checks for path traversal sequences (`..`) before using inputs in API calls.