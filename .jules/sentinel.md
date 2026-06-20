## 2026-06-20 - [Token File Permission CWE-276]
**Vulnerability:** The container launcher wrote sensitive OIDC attestation tokens to a temporary directory with `0755` permissions and the token file itself with `0644` permissions, making the token world-readable to other processes on the host.
**Learning:** Even within an isolated TEE or container environment, defense in depth requires that secrets written to the filesystem follow the principle of least privilege.
**Prevention:** Always use `0700` for secret directories (`os.MkdirAll`) and `0600` for secret files (`os.WriteFile`). Relying on environmental isolation is insufficient.
