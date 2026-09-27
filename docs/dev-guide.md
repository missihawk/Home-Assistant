# Git Tag Quick Reference

## 1. Versioning Logic (`MAJOR.MINOR.PATCH`)

According to semantic versioning rules and tag conventions. [^1]

- **`0.Y.Z` (Pre-1.0.0 / Dev)**: Public API is unstable.
  - PATCH (`0.y.Z`): Backwards-compatible bug fixes or doc updates only.
  - MINOR (`0.Y.0`): Breaking changes (secrets, schemas, directory structure) OR new features.
- **`X.Y.Z` (Production)**: Declares first stable release/schema.
  - PATCH (`x.y.Z`): Backwards-compatible fixes.
  - MINOR (`x.Y.0`): Backwards-compatible new features.
  - MAJOR (`X.0.0`): Breaking API/schema changes.

## 2. Standard Tag Command

```bash
git tag -a vX.Y.Z

```

## 3. Tag Message Template (`TAG_EDITMSG`)

```text
vX.Y.Z - <Short High-Level Milestone Summary>

- Key functional or structural change 1
- Key functional or structural change 2
- ...

NOTE: <Any critical deployment or hardware warnings>

```

---

# Footnotes
[^1]: [Semantic Versioning (SemVer 2.0.0)](https://semver.org/)
