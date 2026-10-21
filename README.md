# CourserLabs/.github

Organization-wide defaults and shared CI for every CourserLabs repository.

| Path | Purpose |
|---|---|
| `profile/README.md` | Public organization profile |
| `SECURITY.md`, `CONTRIBUTING.md` | Default policies for all repos |
| `.github/PULL_REQUEST_TEMPLATE.md`, `.github/ISSUE_TEMPLATE/` | Default PR and issue templates |
| `.github/workflows/security-scan.yml` | Reusable security gate: gitleaks, Semgrep CE, Trivy |
| `.github/workflows/pr-title.yml` | Reusable Conventional Commits PR-title check |
| `renovate-config.json` | Shared Renovate preset |

## Using the shared workflows

```yaml
# <repo>/.github/workflows/security.yml
name: security
on:
  pull_request:
  push:
    branches: [main]
  schedule:
    - cron: '0 6 * * 1'
jobs:
  security:
    uses: CourserLabs/.github/.github/workflows/security-scan.yml@main
```

```json
// <repo>/renovate.json
{ "extends": ["github>CourserLabs/.github:renovate-config"] }
```

This repository is public by design: it holds no secrets, and public reusable workflows can be called
from private repos without extra access settings. Changes here affect every repo, so open a PR, and
consider pinning callers to a tag for risky changes.
