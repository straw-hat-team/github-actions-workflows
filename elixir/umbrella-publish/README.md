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

## Add a HEX API Key to GitHub Secrets

1. Create a [Hex](https://hex.pm) API Key following [Publishing from CI](https://hex.pm/docs/publish#publishing-from-ci)
   .
2. Add the Hex API Key
   to [GitHub Encrypted Secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets)
   named `HEX_API_KEY` (or whichever name you prefer, but stick to the convention if possible).

### Get Started

1. Complete [Add a HEX API Key to GitHub Secrets](#add-a-hex-api-key-to-github-secrets) if required.
2. Make sure `actions/checkout` action is used before this action.
3. Add this action to your job in your workflow, here is an example:

    ```yml
    #...
    jobs:
      publish:
        name: Publish to Hex.pm
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v2 # checkout the repository first
          - uses: straw-hat-team/github-actions-workflows/elixir/umbrella-publish@master
            with:
              elixir-version: '1.11' # optional, fallback to use .tool-versions
              otp-version: '22.3' # optional, fallback to use .tool-versions
              version-type: 'loose' # optional, fallback to strict
              hex-api-key: ${{ secrets.HEX_API_KEY }} # (see step 2)
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
