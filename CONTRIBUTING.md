# Contributing to CourserLabs repositories

These standards apply to every CourserLabs repository. Each repo's `CLAUDE.md` adds its own
stack-specific rules.

## Workflow

1. Branch from `main`: `feat/<short-name>`, `fix/<short-name>`, `chore/<short-name>`.
2. Keep pull requests small, about 400 changed lines or fewer excluding generated files. Split large work.
3. **PR titles follow [Conventional Commits](https://www.conventionalcommits.org/)** (`feat: …`,
   `fix(auth): …`). We squash-merge, so the title becomes the commit message and drives release notes.
4. A PR needs green CI and one approval from a code owner. Every PR an AI agent writes needs human approval.
5. Resolve every review conversation before merging. Don't force-push to `main`.

## Definition of done

- Typecheck, lint, format and tests pass locally (`CLAUDE.md` lists the commands).
- New behavior has tests. A bug fix includes a regression test.
- Schema and API changes are backwards compatible, or the PR description calls them out and explains the migration.
- No secrets, tokens or personal data in code, logs, fixtures or screenshots.
- Docs (README, `CLAUDE.md`, ADRs) are updated when behavior or conventions change.

## Architecture decisions

Record significant decisions as ADRs in `docs/adr/NNNN-title.md`: context, decision, consequences.
Don't edit an accepted ADR. Write a new one that supersedes it.

## Security

- Never commit `.env` files, service-account JSON or credentials. gitleaks blocks them in CI.
- Treat every input as untrusted. Validate at the boundary.
- Report vulnerabilities as described in [SECURITY.md](SECURITY.md).
