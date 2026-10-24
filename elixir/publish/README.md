# Elixir Publish

Publish an Elixir package to Hex.pm.

- [How-to Guides](#how-to-guides)

## How-to Guides

### Get Started

Publishing uses Hex [Workload Identity](https://hex.pm/docs/workload-identity), sometimes also known as Trusted
Publishing, so no Hex API key is stored. It requires Elixir 1.12 and OTP 27 or later. Hex can't create a public package
that way, so publish the first release of a package by hand with `mix hex.publish`.

1. Add a workload identity to the package, or to the organization that owns it, on hex.pm that names the
   repository, the workflow filename, and the GitHub environment of the publishing job.
2. Make sure `actions/checkout` action is used before this action.
3. Give the job that environment and the `id-token: write` permission, here is an example:

    ```yml
    jobs:
      publish:
        name: Publish to Hex.pm
        runs-on: ubuntu-latest
        environment: hexpm
        permissions:
          contents: read
          id-token: write
        steps:
          - uses: actions/checkout@v2 # checkout the repository first
          - uses: straw-hat-team/github-actions-workflows/elixir/publish@master
    ```
