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

This repository contains reusable workflows and composite actions for CI/CD automation across Hlavi projects.

### Structure

```
.github/
├── actions/
│   ├── setup-rust/
│   │   └── action.yml          # Install Rust toolchain with caching
│   ├── rust-lint/
│   │   └── action.yml          # Run cargo fmt and clippy
│   ├── rust-test/
│   │   └── action.yml          # Run tests with optional coverage
│   └── rust-build/
│       └── action.yml          # Build for specific target
└── workflows/
    ├── rust-ci.yml             # Complete CI pipeline
    ├── rust-version-bump.yml   # Automated version bumping
    └── rust-release-binary.yml # Cross-platform binary building
```

## Development

Information on how to go about your development workflow.

## Contributing

Take a moment to review our [contribution guide](CONTRIBUTING.md) before submitting your first pull request.

Make sure that you check for open issues and pull requests to see if someone else is working on something similar.

## Contact

For feedback, requests or enquiries:

🌐 [http://www.mmuhlariholdings.co.za](http://www.mmuhlariholdings.co.za)
