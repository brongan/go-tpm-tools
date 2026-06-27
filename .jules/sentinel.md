## 2026-06-27 - [MEDIUM] Fix insecure file and directory permissions (CWE-276)
**Vulnerability:** The launcher was creating temporary directories and sensitive token files with overly permissive permissions (`0755` for directories, `0644` for files). This can lead to CWE-276, exposing sensitive information to unauthorized local users.
**Learning:** In Go, functions like `os.MkdirAll` and `os.WriteFile` require explicit secure permission masks. Defaulting to standard permissions like `0644` or `0755` is dangerous for sensitive tokens and their parent directories.
**Prevention:** Always use strict permissions for sensitive data: `0700` for directories and `0600` for files. Run static analysis tools like `gosec` to automatically detect insecure permissions.
