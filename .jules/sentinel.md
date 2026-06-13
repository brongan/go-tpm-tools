## 2026-06-13 - [Insecure File Permissions for Token and Temporary Directory]
**Vulnerability:** Found CWE-276 vulnerabilities in `launcher/container_runner.go`. Token file was created with `0644` permissions, and temporary host directory for tokens was created with `0755` permissions. This could potentially allow other local users to read sensitive token data.
**Learning:** `os.WriteFile` and `os.MkdirAll` calls handling sensitive token info were defaulting to permissive file modes which violates security principle of least privilege.
**Prevention:** Ensure tightest possible permissions on sensitive material: `0600` for files containing secrets, and `0700` for their parent directories. Use `gosec` as an automated hook to catch `G301` and `G306` insecure permission calls early.
