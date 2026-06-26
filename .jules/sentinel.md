## 2026-06-26 - [Insecure File Permissions on Temporary Token]
**Vulnerability:** A temporary token file and its parent directory in `launcher/container_runner.go` were being created with weak permissions (`0644` for the file and `0755` for the directory), making sensitive secrets readable by any user on the system (CWE-276).
**Learning:** Even when files are stored in temporary directories, the files themselves and the temporary directories must explicitly declare restrictive permissions if they contain sensitive data. Default permissive modes are dangerous.
**Prevention:** Always use restrictive modes like `0600` for files containing secrets and `0700` for directories housing them. Use static analysis tools like `gosec` to identify weak permissions dynamically.
