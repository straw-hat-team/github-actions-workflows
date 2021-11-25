# GitHub Actions Workflows

A set of GitHub Actions Workflow Templates.

## Elixir

### Elixir Hex Publish

```yaml
name: Hex Publish

on:
  release:
    types: [published]

jobs:
  publish-to-hex-pm:
    uses: straw-hat-team/github-actions-workflows/.github/workflows/elixir-hex-publish.yml@master
    with:
      elixir-version: '...'
      otp-version: '...'
    secrets:
      HEX_API_KEY: ${{ secrets.HEX_API_KEY }}
```
