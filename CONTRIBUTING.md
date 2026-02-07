# Contributing Guidelines

To keep our workflow consistent, please follow these conventions when creating branches, commits, and pull requests.

## Branch Naming

Branches must follow this pattern:

```bash
<type>/<ticket-id>-<short-summary>
```

or if no ticket exists:

```bash
<type>/<short-summary>
```

### Types

- **feature** → new workflow or action
- **fix** → bug fix in existing workflow
- **chore** → maintenance or tooling
- **docs** → documentation only
- **refactor** → workflow restructuring

### Examples

- `feature/HLAVI-100-Add-Node-CI-Workflow`
- `fix/HLAVI-101-Release-Binary-ARM64`
- `docs/Update-Usage-Examples`

### Notes:

- Include the ticket ID if available (future: HLAVI-XXX, currently optional)
- Use Pascal-Case or hyphenated words for the summary
- Keep summaries concise but descriptive
- All feature branches merge into `main` via Pull Request

## Commit Message Convention

Commit messages must follow this style:

```bash
<type>: <short summary>
```

or with ticket ID:

```bash
<type>(TICKET-ID): <short summary>
```

### Types

- **feature** → new workflow or action
- **fix** → bug fix
- **chore** → maintenance
- **docs** → documentation
- **refactor** → workflow restructuring

### Examples

- `feature: add Node.js CI workflow`
- `fix(HLAVI-101): correct ARM64 Linux build in release workflow`
- `docs: update usage examples for rust-ci workflow`
- `refactor: extract common build steps into composite action`

### Notes:

- Use imperative mood in the summary (add, fix, update)
- Keep summaries concise (< 72 characters)
- Ticket ID optional until tracking system is finalized

## Pull Request Titles

PR titles must follow this pattern:

```bash
[XX] <ticket-id>: <short summary>
```

or without ticket:

```bash
[XX] <short summary>
```

### Where:

- **XX** → Your initials (first 2 characters of first name + surname)
- **ticket-id** → Optional ticket identifier (e.g., HLAVI-100)
- **short summary** → Description of the completed work

### Examples

- `[MaMu] HLAVI-100: Added Node.js CI Workflow`
- `[MaMu] Fix ARM64 Linux release build`

### Notes:

- Use past tense for the summary (describes what was done)
- Keep summaries under 70 characters
- Link to ticket in PR description when available

## Testing Workflows

Before submitting a PR:

1. **Test in a branch of a consuming repository** (hlavi-cli, hlavi-core, etc.)
2. **Update the workflow reference** to your branch:
   ```yaml
   uses: mmuhlariholdings/hlavi-workflows/.github/workflows/rust-ci.yml@your-branch-name
   ```
3. **Verify all jobs pass** in the consuming repository
4. **Revert the reference to @main** before merging

## Versioning

Once workflows are stable, tag releases for version pinning:

```bash
git tag -a v1.0.0 -m "Release v1.0.0"
git push origin v1.0.0
```

Consuming repositories can then pin to specific versions:

```yaml
uses: mmuhlariholdings/hlavi-workflows/.github/workflows/rust-ci.yml@v1.0.0
```

## Impact Analysis

Changes to reusable workflows affect all consuming repositories:

### Consuming Repositories:
- **hlavi-core** - Core library
- **hlavi-agent** - AI agent library
- **hlavi-cli** - Command-line interface
- **hlavi-api** - HTTP API server
- **hlavi-web** - Web application (future)
- **hlavi-app** - Desktop application (future)

Always consider backward compatibility when making changes.

## Protected Branch Rules

The `main` branch is protected:

- ✅ Requires pull request reviews before merging
- ✅ Requires status checks to pass
- ✅ Requires branches to be up to date before merging
- ✅ Requires conversation resolution before merging
- ❌ Direct pushes not allowed
- ❌ Force pushes not allowed

## Questions?

If you have questions about contributing, please:
- Check existing issues and PRs
- Ask in GitHub Discussions
- Contact maintainers

Thank you for contributing to Hlavi! 🚀
