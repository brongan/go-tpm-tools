## 2026-06-25 - [Insecure File Permissions for Tokens]
**Vulnerability:** Temporary token directories and files were created with overly permissive permissions (0755 and 0644) instead of strict owner-only permissions (0700 and 0600).
**Learning:** This could allow unintended access or modification by other processes running as different users on the system, which is a critical risk for sensitive token files used by the container launcher.
**Prevention:** Always use restrictive file permissions ( for sensitive directories,  for sensitive files) when calling  or , as identified by gosec rules G301 and G306.
## 2025-02-20 - [Insecure File Permissions for Tokens]
**Vulnerability:** Temporary token directories and files were created with overly permissive permissions (0755 and 0644) instead of strict owner-only permissions (0700 and 0600).
**Learning:** This could allow unintended access or modification by other processes running as different users on the system, which is a critical risk for sensitive token files used by the container launcher.
**Prevention:** Always use restrictive file permissions (0700 for sensitive directories, 0600 for sensitive files) when calling os.MkdirAll or os.WriteFile, as identified by gosec rules G301 and G306.
