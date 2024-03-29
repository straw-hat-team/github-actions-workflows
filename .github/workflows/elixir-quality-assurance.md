# Elixir Quality Assurance

Enables Quality Assurance tools

- [How-to Guides](#how-to-guides)
- [Explanations](#explanations)

## Explanations

This workflow is a suit of development tool setup for Elixir projects that leverage other actions such as:

- [elixir/credo](../../elixir/credo/README.md) for linting check.
- [elixir/dialyzer](../../elixir/dialyzer/README.md) for typespec check.
- [elixir/format](../../elixir/format/README.md) for formatting check.
- [elixir/test](../../elixir/test/README.md) for testing check.
- [elixir/compilation-warnings](../../elixir/compilation-warnings/README.md) for compilation warning check.

You can disable these actions by changing the setting the workflow. Please check the workflow input documentation.

## How-to Guides

### Get Started

1. Create a new GitHub Workflow (ex: `.github/workflows/ci.yml`) if you don't have one already.
3. Add the following this workflow to your workflow, here is a final example:

```yaml
name: Elixir Quality Assurance

on:
  push:
    branches:
      - master
  pull_request:
    branches:
      - master

jobs:
  quality-assurance:
    uses: straw-hat-team/github-actions-workflows/.github/workflows/elixir-quality-assurance.yml@master
    with:
      elixir-version: '1.11' # optional, fallback to use .tool-versions
      otp-version: '22.3' # optional, fallback to use .tool-versions
      version-type: 'loose' # optional, fallback to strict
      testing-enabled: true # or false to disable it
      formatter-enabled: true
      credo-enabled: true
      dialyzer-enabled: true
      compilation-warning-enabled: true
```
