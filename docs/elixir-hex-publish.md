# Elixir Hex Publish

Publish Elixir packages to https://hex.pm/.

## Usage

Create a [Hex](https://hex.pm) API Key following [Publishing from CI](https://hex.pm/docs/publish#publishing-from-ci).

Add the Hex API Key to [GitHub Encrypted Secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets)
named `HEX_API_KEY`.

Create a new GitHub Workflow (ex: `.github/workflows/cd.yml`) with the following content:

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
