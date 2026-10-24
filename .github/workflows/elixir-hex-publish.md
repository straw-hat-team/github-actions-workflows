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

1. Complete [Get Started](../../elixir/publish/README.md#get-started) from
   [elixir/publish](../../elixir/publish/README.md). The workflow filename the identity names is your workflow that calls
   this one, not `elixir-hex-publish.yml`.
2. Create a new GitHub Workflow (ex: `.github/workflows/cd.yml`) if you don't have one already.
3. Grant the calling job `id-token: write` and pass the environment the identity names, here is a final example:

```yaml
name: Hex Publish

on:
  release:
    types: [ published ]

jobs:
  publish-to-hex-pm:
    permissions:
      contents: read
      id-token: write
    uses: straw-hat-team/github-actions-workflows/.github/workflows/elixir-hex-publish.yml@master
    with:
      environment: hexpm
      elixir-version: '1.18' # optional, fallback to use .tool-versions
      otp-version: '27.3' # optional, fallback to use .tool-versions
      version-type: 'loose' # optional, fallback to strict
```
