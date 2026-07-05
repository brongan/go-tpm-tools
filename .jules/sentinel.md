## 2026-07-05 - Insecure File and Directory Permissions (CWE-276)
**Vulnerability:** The launcher token temp directory and the temp token file itself were created with overly permissive permissions (`0755` and `0644` respectively). This could allow local attackers to read sensitive attestation tokens if they have access to the host filesystem.
**Learning:** `gosec` surfaces CWE-276 issues for sensitive files like tokens or credentials. Even temporary paths need strict permissions because race conditions or container escapes could expose them.
**Prevention:** When creating directories or files that will store sensitive tokens or credentials, strictly use `0700` for directories and `0600` for files.
