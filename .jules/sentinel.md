## 2026-06-29 - Fixed Insecure Token File Permissions

**Vulnerability:** The `container_runner.go` code in the `launcher` module was creating a temporary directory with `0755` permissions and writing an authentication token file with `0644` permissions, making the sensitive token world-readable.
**Learning:** Even temporary files used to store sensitive data like authentication tokens must be protected with strict `0600` permissions, and their containing directories with `0700`. This prevents other users on the host system from reading the token before it is moved to its final destination.
**Prevention:** Always use `0600` for files containing secrets and `0700` for directories containing them. Use static analysis tools like `gosec` to detect insecure file permissions (CWE-276).
