# GitHub Actions Workflows

A set of GitHub Actions Workflow Templates.

## Elixir

### Elixir Hex Publish

Publish Elixir packages to https://hex.pm/.

```yaml
name: Hex Publish

on:
  release:
    types: [published]

jobs:
  publish-to-hex-pm:
    uses: straw-hat-team/github-actions-workflows/.github/workflows/elixir-hex-publish.yml@master
    with:
      elixir-version: '1.11'
      otp-version: '22.3'
    secrets:
      HEX_API_KEY: ${{ secrets.HEX_API_KEY }}
```

### Elixir Quality Assurance All

Enables all the Quality Assurance tools:

- Testing (mix test)
- Formatter (mix format)
- Linter (mix credo)
- Typespec (mix dialyzer)

```yaml
name: Hex Publish

on:
  release:
    types: [published]

jobs:
  publish-to-hex-pm:
    uses: straw-hat-team/github-actions-workflows/.github/workflows/elixir-quality-assurance-all.yml@master
    with:
      elixir-version: '1.11'
      otp-version: '22.3'
```
