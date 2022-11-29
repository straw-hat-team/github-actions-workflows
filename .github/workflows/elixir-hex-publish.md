# Elixir Hex Publish

Publish Elixir packages to https://hex.pm/.

- [How-to Guides](#how-to-guides)
- [Explanations](#explanations)

## Explanations

This workflow is based on the [elixir/publish](../../elixir/publish/README.md) Action. Removes the needs to worry about
checking out the source code. It is meant to be the fastest and less error-prone way to publish your packages for the
95% of the cases.

## How-to Guides

### Get Started

1. Complete [Add a HEX API Key to GitHub Secrets](../../elixir/publish/README.md#add-a-hex-api-key-to-github-secrets) if
   required from [elixir/publish](../../elixir/publish/README.md).
2. Create a new GitHub Workflow (ex: `.github/workflows/cd.yml`) if you don't have one already.
3. Add the following this workflow to your workflow, here is a final example:

```yaml
name: Hex Publish

on:
  release:
    types: [ published ]

jobs:
  publish-to-hex-pm:
    uses: straw-hat-team/github-actions-workflows/.github/workflows/elixir-hex-publish.yml@master
    with:
      elixir-version: '1.11' # optional, fallback to use .tool-versions 
      otp-version: '22.3' # optional, fallback to use .tool-versions
      version-type: 'loose' # optional, fallback to strict
    secrets:
      HEX_API_KEY: ${{ secrets.HEX_API_KEY }}
```
