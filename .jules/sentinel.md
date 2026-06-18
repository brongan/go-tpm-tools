## 2025-02-13 - [Insecure File Permissions]
**Vulnerability:** CWE-276: Insecure directory and file permissions were discovered in `launcher` token handling (`0644` for files and `0755` for directories).
**Learning:** Hardcoded permissions in directory/file creations can expose sensitive tokens and application states if too broad.
**Prevention:** Use strictly restricted file/directory creation permissions (`0600` for files containing secrets, `0700` for directories). Utilize tools like `gosec` to automatically detect unsafe permissions.
