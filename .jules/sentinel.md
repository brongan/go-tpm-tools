## 2026-06-23 - Overly Permissive Token Directory and File
**Vulnerability:** The temporary attestation token file was being written with `0644` permissions, and its parent directory created with `0755`.
**Learning:** These permissions expose sensitive JWT tokens to unauthorized users on the same host system, which could lead to token theft and unauthorized access.
**Prevention:** Always use restrictive permissions when dealing with sensitive files (`0600`) and directories (`0700`).
