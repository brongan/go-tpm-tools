## 2024-05-19 - Fixed CWE-276 Insecure File/Directory Permissions in Launcher
**Vulnerability:** The launcher module created sensitive temporary directories (`os.MkdirAll`) with `0755` permissions and wrote sensitive OIDC token files (`os.WriteFile`) with `0644` permissions. This allowed other users on the system to potentially read the token.
**Learning:** Hardcoded permissions in Go standard library calls often default to insecure values if not explicitly scoped down. The `gosec` tool (specifically rules G301 and G306) accurately identifies these.
**Prevention:** Always use `0700` for sensitive directories and `0600` for sensitive files containing secrets, credentials, or tokens.
