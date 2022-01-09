# Elixir Hex Publish

Publish Elixir packages to https://hex.pm/. Uses the [elixir/publish](../../elixir/publish/README.md) Action.

## How-to Guides

### Get Started

1. Complete [Add a HEX API Key to GitHub Secrets](../../elixir/publish/README.md#add-a-hex-api-key-to-github-secrets) if
   required from [elixir/publish](../../elixir/publish/README.md).
2. Create a new GitHub Workflow (ex: `.github/workflows/cd.yml`) with the following job:

```yaml
name: Hex Publish

on:
  release:
    types: [ published ]

jobs:
  publish-to-hex-pm:
    uses: straw-hat-team/github-actions-workflows/.github/workflows/elixir-hex-publish.yml@master
    with:
      elixir-version: '1.11'
      otp-version: '22.3'
    secrets:
      HEX_API_KEY: ${{ secrets.HEX_API_KEY }}
```
