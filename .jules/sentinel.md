## 2026-06-17 - Insecure Default Permissions for Temporary Token Files

**Vulnerability:** The launcher module created sensitive temporary directories (`launcherfile.HostTmpPath`) with `0755` permissions and wrote the attestation verifier token to a temporary file with `0644` permissions (CWE-276).
**Learning:** These loose permissions could allow unauthorized local processes or users inside the environment to access or read sensitive token material.
**Prevention:** Always use restrictive permissions, e.g., `0700` for sensitive directories and `0600` for files containing secrets or tokens.
