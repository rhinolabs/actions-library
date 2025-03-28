# GitHub Actions Reusable Workflows Library

A collection of reusable GitHub Actions workflows for Node.js/TypeScript/React projects.

## 📋 Available Workflows

### JavaScript/TypeScript Workflows

- **[CI Workflow](workflows/nodejs/ci.yml)**: Lint, test, and build Node.js/TypeScript/React projects

## 🚀 How to Use

These workflows are designed to be reusable across repositories. You can call them from your own GitHub Actions workflows.

### Example: Using the Node.js CI Workflow

Create a `.github/workflows/ci.yml` file in your repository:

```yaml
name: CI

on:
  pull_request:
    branches: [main]
  push:
    branches: [main]

jobs:
  lint-test-build:
    uses: rhinolabs/actions-library/workflows/nodejs/ci.yml@v1
    with:
      node-version: '22'
      package-manager: 'bun'
      lint-command: 'lint'
      test-command: 'test'
      build-command: 'build'
```

## 📖 Workflow Documentation

### Node.js CI Workflow

The [Node.js CI Workflow](workflows/nodejs/ci.yml) provides a configurable pipeline for linting, testing, and building Node.js/TypeScript/React projects.

**Inputs:**

| Name | Description | Default | Required |
|------|-------------|---------|----------|
| `node-version` | Node.js version to use | `'18'` | No |
| `package-manager` | Package manager (npm, yarn, pnpm, bun) | `'npm'` | No |
| `lint-command` | Command to run linting | `'lint'` | No |
| `test-command` | Command to run tests | `'test'` | No |
| `build-command` | Command to run build | `'build'` | No |
| `enable-test` | Enable test step | `true` | No |
| `enable-lint` | Enable lint step | `true` | No |
| `enable-build` | Enable build step | `true` | No |

## 📦 Versioning

This repository uses [GitHub's Release Drafter](https://github.com/release-drafter/release-drafter) to manage releases and versioning automatically:

- Version numbers follow [Semantic Versioning](https://semver.org/) (`MAJOR.MINOR.PATCH`)
- Release Drafter automatically determines the next version number based on PR labels:
  - `breaking`: Triggers a MAJOR version bump
  - `enhancement`: Triggers a MINOR version bump
  - All other changes: PATCH version bump

### Using Specific Versions

When using these workflows in your repository, you can specify:

```yaml
# Latest from main branch (not recommended for production)
uses: rhinolabs/actions-library/workflows/nodejs/ci.yml@main

# Specific version (recommended for stability)
uses: rhinolabs/actions-library/workflows/nodejs/ci.yml@v1.0.0

# Latest minor version (good balance of stability and features)
uses: rhinolabs/actions-library/workflows/nodejs/ci.yml@v1
```

## 🛠️ Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request with appropriate labels:
   - `breaking`: For backwards-incompatible changes
   - `enhancement`: For new features and improvements
