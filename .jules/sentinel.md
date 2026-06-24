## 2026-06-24 - [Insecure File Permissions]
**Vulnerability:** Found CWE-276 vulnerabilities in `launcher` module where temporary directories and auth tokens were created with overly permissive file permissions (`0644` for tokens and `0755` for directories).
**Learning:** Hardcoded permissions in testing code and application code must be monitored, as permissions like `0644` or `0755` can expose sensitive information or allow privilege escalation.
**Prevention:** Always use the most restrictive permissions necessary, such as `0600` for sensitive files and `0700` for directories handling temporary secrets.
