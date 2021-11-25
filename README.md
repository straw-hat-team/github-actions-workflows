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
      testing_enabled: true
      formatter_enabled: true
      linter_enabled: true
      typespec_enabled: true
```

#### Dialyzer setup

You must configure Dialyzer as follow:

```elixir
def project do
  [
    dialyzer: [
      plt_core_path: "priv/plts",
      plt_file: {:no_warn, "priv/plts/dialyzer.plt"}
    ]
  ]
end
```
