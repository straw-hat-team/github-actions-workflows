# Elixir Publish

Publish an Elixir package to Hex.pm.

## Usage

Create a [Hex](https://hex.pm) API Key following [Publishing from CI](https://hex.pm/docs/publish#publishing-from-ci).

Add the Hex API Key to [GitHub Encrypted Secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets)
named `HEX_API_KEY` (or whichever name you prefer).

```yml
#...
jobs:
  publish:
    name: Publish to Hex.pm
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: straw-hat-team/github-actions-workflows/elixir-publish@master
        with:
          elixir-version: '1.11'
          otp-version: '22.3'
          hex-api-key: ${{ secrets.HEX_API_KEY }}
```
