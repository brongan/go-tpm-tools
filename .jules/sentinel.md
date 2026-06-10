## 2024-05-18 - Fix Insecure File Permissions in launcher
**Vulnerability:** GoSec reported CWE-276 (insecure file permissions) on token directory creation and token file write in launcher/container_runner.go.
**Learning:** Files containing tokens should be restricted. A token write permissions to 0600 instead of 0644 avoids leaking it to other users.
**Prevention:** Follow least-privilege for directories and sensitive files. For dirs, 0700 or 0750. For sensitive files, 0600.
