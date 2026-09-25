# Contributing guidelines

## Languages

- Code, commit messages, branch names, pull requests and technical documentation: **English**.
- Issues and functional documentation (`docs/expression-des-besoins.md`, `docs/journal-de-projet.md`): **French**.
- Labels and milestones: **English**.

## Branching model (GitHub Flow)

- `main` is always stable and never receives direct commits.
- Each issue is developed on a short-lived branch created from an up-to-date `main`.
- Branch naming: `<type>/<issue-number>-<short-description>`, e.g. `feature/12-product-search`.
- Allowed types: `feature`, `fix`, `docs`, `refactor`, `test`, `chore`.

## Commit messages (Conventional Commits)

Format: `<type>(<optional scope>): <description>`

| Type | Usage |
|---|---|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `style` | Formatting, no code change |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `test` | Adding or updating tests |
| `chore` | Maintenance, configuration, dependencies |
| `build` / `ci` | Build system or continuous integration |
| `perf` | Performance improvement |

Rules: imperative mood, lowercase, no trailing period, 72 characters maximum.

Examples:
- `feat(api): add product search endpoint`
- `fix(front): keep selected filters after page reload`
- `test(db): cover price-per-kg calculation`

## Pull requests

- One pull request per issue; the title follows the Conventional Commits format.
- Link the issue in the description with `Closes #<issue-number>`.
- Fill in the pull request template and review your own diff before merging.
- All checks must pass.
- Merge with **Squash and merge**; the branch is deleted automatically.

## Definition of done

An issue is done when:
- its acceptance criteria are met;
- tests are written and passing;
- the linter reports no errors;
- documentation is up to date;
- the project journal is updated for significant changes.