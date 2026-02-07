# hlavi-workflows

Shared GitHub Actions workflows for all Hlavi projects.

## Table of Contents

- [Getting Started](#getting-started)
- [Documentation](#documentation)
- [Development](#development)
- [Contributing](#contributing)
- [Contact](#contact)

## Getting Started

A quick guide on how you can get started running and working on the applicatoin on your local machine.

### Requirements

- GitHub repository with Actions enabled
- Rust projects using Cargo (for Rust workflows)
- Access to this repository (public or granted if private)

### Clone

```bash
git clone https://github.com/mmuhlariholdings/hlavi-workflows.git
cd hlavi-workflows
```

### Usage

Reference workflows from your project's `.github/workflows` directory:

```yaml
jobs:
  ci:
    uses: mmuhlariholdings/hlavi-workflows/.github/workflows/rust-ci.yml@main
```

## Documentation

This repository contains reusable workflows for CI/CD automation across Hlavi projects.

### Available Workflows

**rust-ci.yml** - Complete CI pipeline for Rust projects
- Formatting check with `cargo fmt`
- Linting with `cargo clippy`
- Tests on Linux, macOS, and Windows
- Cross-platform builds

**rust-version-bump.yml** - Automated version bumping
- Semantic versioning (patch, minor, major)
- Git tagging and release creation
- Cargo.toml and Cargo.lock updates

**rust-release-binary.yml** - Cross-platform binary building
- Builds for Linux, macOS, Windows (AMD64 and ARM64)
- Archive creation and release asset uploading

### Example Usage

**CI Workflow:**
```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  ci:
    uses: mmuhlariholdings/hlavi-workflows/.github/workflows/rust-ci.yml@main
```

**Version Bump Workflow:**
```yaml
name: Version Bump

on:
  workflow_dispatch:
    inputs:
      version_type:
        type: choice
        options: [patch, minor, major]

jobs:
  bump:
    uses: mmuhlariholdings/hlavi-workflows/.github/workflows/rust-version-bump.yml@main
    with:
      version-type: ${{ github.event.inputs.version_type }}
      package-name: 'your-package-name'
    secrets:
      github-token: ${{ secrets.GITHUB_TOKEN }}
```

**Release Workflow:**
```yaml
name: Release

on:
  push:
    tags: ['v*']

jobs:
  release:
    uses: mmuhlariholdings/hlavi-workflows/.github/workflows/rust-release-binary.yml@main
    with:
      binary-name: 'your-binary-name'
    secrets:
      github-token: ${{ secrets.GITHUB_TOKEN }}
```

## Development

Information on how to go about your development workflow.

## Contributing

Take a moment to review our [contribution guide](CONTRIBUTING.md) before submitting your first pull request.

Make sure that you check for open issues and pull requests to see if someone else is working on something similar.

## Contact

For feedback, requests or enquiries:

🌐 [http://www.mmuhlariholdings.co.za](http://www.mmuhlariholdings.co.za)
