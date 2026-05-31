# Renovate organization preset

WebGrip repositories can extend the organization default Renovate preset from the `.github` repository:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>webgrip/.github"]
}
```

The preset is intentionally conservative:

- non-security updates require explicit Dependency Dashboard approval before Renovate opens a PR
- automerge is disabled
- update PR creation is limited to early Monday mornings in the Europe/Amsterdam timezone
- new releases must be at least seven days old before they are proposed
- PR concurrency is limited to reduce update noise
- Docker images and GitHub Actions are pinned to immutable digests
- peer dependency updates are disabled by default

Repositories can still add local `packageRules` after extending this preset when they need a narrower exception.
