# Elixir Publish

Publish an Elixir package to Hex.pm.

- [How-to Guides](#how-to-guides)

## How-to Guides

### Get Started

1. Create a [Hex](https://hex.pm) API Key following [Publishing from CI](https://hex.pm/docs/publish#publishing-from-ci).

2. Add the Hex API Key to [GitHub Encrypted Secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets)
named `HEX_API_KEY` (or whichever name you prefer).

3. Add the job to your workflow:

  ```yml
  #...
  jobs:
    publish:
      name: Publish to Hex.pm
      runs-on: ubuntu-latest
      steps:
        - uses: actions/checkout@v2 # checkout the repository first
        - uses: straw-hat-team/github-actions-workflows/elixir/publish@master
          with:
            elixir-version: '1.11'
            otp-version: '22.3'
            hex-api-key: ${{ secrets.HEX_API_KEY }} # (see step 2)
  ```
