# Elixir Umbrella Publish

Publish an Elixir package to Hex.pm from an Umbrella app setup.

- [How-to Guides](#how-to-guides)
- [Explanations](#explanations)

## Explanations

### Ref Name Configuration

`ref-name` configuration is used to identify which package you suppose to release. When the `ref-name` matches the
following regex `^(.+)\@v([0-9]+\.[0-9]+\.[0-9])$` which is `[package-name]@v[version]`, the package will be published
to Hex.pm if the package exists under the umbrella setup, and the version matches the existing package version in
the `mix.exs` file.

For conveniently, the `ref-name` value could be read from `${{ github.ref_name }}` context when reacting to a release
event.

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
          - uses: straw-hat-team/github-actions-workflows/elixir/umbrella-publish@master
            with:
              ref-name: ${{ github.ref_name }} # the GitHub Release Tag Name with the format of "[package name]@v[version]"
    ```

### Fix ExDoc GitHub Linking

1. Open the `mix.exs` file of the package you want to publish.
2. Setup `source_url_pattern` of `docs` as follows:
    
    ```elixir
    defmodule MyPkgName.MixProject do
      use Mix.Project
      
      @app :my_pkg_name
      @version "0.7.3"
      @source_url "https://github.com/{owner}/{repo}"
      
      def project do
        [
          # ...
          docs: [
           source_url_pattern: "#{@source_url}/blob/#{@app}@v#{@version}/apps/#{@app}/%{path}#L%{line}"
          ],
        ]
      end
    end
    ```
