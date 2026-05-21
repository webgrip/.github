# Governance

This document describes how the webgrip organisation makes decisions, how contributions are evaluated, and what you can expect when engaging with projects here.

---

## 🏛️ Model: Benevolent Dictator with Open Input

Webgrip is a small, opinionated organisation. Final decisions on direction, merges, and architecture rest with the primary maintainer — **Ryan Grippeling** ([@Ryangr0](https://github.com/Ryangr0)). This is not a committee; decisions are made by one person who is accountable for the outcomes.

This does **not** mean contributions or feedback are ignored. It means there is a clear decision-maker, which keeps things moving.

---

## 🧭 Core Decision Principles

Every significant decision — technical or otherwise — is evaluated against these values, in rough order of priority:

1. **Ethics first** — Does this respect user privacy, avoid harm, and align with the [Ethics statement](./ETHICS.md)?  
2. **Reversibility** — Can we undo this easily? Prefer changes with a clear rollback path.
3. **Minimal footprint** — Do one thing well. Avoid scope creep and unnecessary complexity.
4. **Clear ownership** — There should be one obvious place where a configuration or behaviour lives.
5. **Auditability** — Changes should be traceable. GitOps, signed commits, and explicit manifests are preferred over imperative one-offs.
6. **Security by default** — Secrets stay out of git. Least-privilege everywhere. SOPS over plaintext.

---

## 📦 Repository Lifecycle

Projects in this organisation may be in one of several states:

| Status | Meaning |
|---|---|
| **Active** | Maintained, accepting contributions and issues |
| **Experimental** | Early-stage, breaking changes expected, no stability guarantee |
| **Archived** | Read-only, not maintained, kept for reference |
| **Internal** | Private or internal tooling, not accepting external contributions |

The README of each repository indicates its current state.

---

## 🔀 How Changes Get Made

### Trivial changes (typos, dependency bumps, config tweaks)
Open a PR directly. No prior discussion needed. Renovate handles most dependency updates automatically.

### Small features or improvements
Open an **Ideas** discussion or a GitHub Issue describing what you want to change and why. If there's agreement in principle, open a PR.

### Significant architectural changes
Start with a **Discussion** or an **Issue** before writing code. Explain the problem, your proposed approach, and the trade-offs. Changes that affect GitOps structure, security posture, or cross-cutting behaviour require explicit sign-off before a PR will be merged.

### Breaking changes
Breaking changes must be documented with a migration path. For infrastructure repos, a breaking change is one that requires manual intervention during a Flux reconciliation or Helm upgrade.

---

## 🤝 Contribution Review

All PRs are reviewed against:

- Does it align with the project's purpose?
- Is it reversible?
- Does it introduce new secrets, credentials, or sensitive data into version control?
- Does it follow the existing code style and patterns in that repo?
- Is it tested or validated (where applicable)?

PRs that embed secrets, bypass GitOps patterns, or introduce irreversible changes without documentation will not be merged.

---

## 🔐 Security and Secrets

The organisation follows a strict no-secrets-in-git policy:

- All secrets are encrypted with [SOPS](https://github.com/getsops/sops) before committing
- PRs introducing plaintext credentials will be closed immediately and the credentials rotated
- Security issues must be reported privately — see [SECURITY.md](./SECURITY.md)

---

## 🤖 AI-Augmented Workflows

Webgrip uses GitHub Copilot agents, custom prompts, and AI tooling as part of normal development. This means:

- Some PRs or commit messages may be AI-assisted
- AI-generated changes are still held to the same review standards as human-written changes
- AI tools operate within the same GitOps constraints — no imperative cluster changes without a manifest trail

---

## 📣 Announcements and Roadmap

Significant updates, roadmap changes, and releases are announced in **GitHub Discussions** under the **Announcements** category. There is no mailing list or external newsletter.

---

## 🗳️ Conflict Resolution

If you disagree with a decision:

1. Say so clearly and calmly in the relevant Issue or Discussion, with reasoning
2. The maintainer will respond and explain the decision
3. The maintainer's decision is final

Personal attacks, entitlement, or harassment result in immediate removal from the community — see [Code of Conduct](./CODE_OF_CONDUCT.md).

---

## 📋 Changes to This Document

Changes to governance are made by the primary maintainer and announced in Discussions. Community input is welcome before finalisation.

---

*Last updated by [@Ryangr0](https://github.com/Ryangr0)*
