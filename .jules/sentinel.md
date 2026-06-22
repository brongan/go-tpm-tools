## 2026-06-22 - [Insecure Temporary File Permissions in Launcher]
**Vulnerability:** Insecure file creation permissions (CWE-276) where temporary token files were created with world-readable permissions (0644) and their parent directories with 0755 in launcher/container_runner.go.
**Learning:** This existed because standard temporary directory creation patterns were used without evaluating the sensitive nature of the contents (attestation tokens). A world-readable token on a host environment is a major credential exposure risk.
**Prevention:** When creating files containing sensitive tokens or credentials, always explicitly apply strict permissions (0600 for files, 0700 for directories). Additionally, use gosec scans to routinely identify G301 and G306 rule violations across the project.
