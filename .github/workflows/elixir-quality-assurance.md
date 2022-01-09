# Elixir Quality Assurance

Enables Quality Assurance tools:

- Testing (mix test)
- Formatter (mix format)
- Linter (mix credo)
- Typespec (mix dialyzer)

- [How-to Guides](#how-to-guides)
- [Explanations](#explanations)

## Explanations

This workflow is a suit of development tool setup for Elixir projects that leverage other actions such as:

- [nodejs/prettier](../../nodejs/prettier/README.md) for code formatting.
- [nodejs/jest](../../nodejs/jest/README.md) for testing.

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
      elixir-version: '1.11'
      otp-version: '22.3'
      testing-enabled: true
      formatter-enabled: true
      credo-enabled: true
      dialyzer-enabled: true
```
