## 2024-05-18 - Fix Insecure Temporary File Permissions
**Vulnerability:** Temporary directory for container tokens (`HostTmpPath`) was created with `0755` (world-readable/executable) and tokens were written with `0644` (world-readable).
**Learning:** Security-sensitive temporary files and directories need to have strict permissions to prevent unauthorized access or modification, avoiding default permissive permissions like `0755` or `0644`.
**Prevention:** Always verify file and directory creation permissions and use `0700`/`0600` or tighter for sensitive data. Utilize gosec checks.
