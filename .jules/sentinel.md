## 2024-05-24 - [Insecure Token Permissions]
**Vulnerability:** Temporary token files in the launcher container runner were written with world-readable (0644) permissions, and the containing directory with 0755 permissions. This violates the principle of least privilege for sensitive authentication materials.
**Learning:** Default permissions used with `os.MkdirAll` and `os.WriteFile` often default to too-permissive values (0755/0644). Explicitly restricting to owner-only access is crucial when handling secrets like JWT tokens.
**Prevention:** Always use `0600` for sensitive files and `0700` for their containing directories when writing directly to disk. Use static analysis tools like `gosec` to automatically surface G301 and G306 rule violations.
