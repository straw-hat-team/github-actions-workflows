# Elixir Compilation Warnings

Compiles the code treating warnings as errors.

- [How-to Guides](#how-to-guides)

## How-to Guides

### Get Started

1. Make sure `actions/checkout` action is used before this action.
2. Add this action to your job in your workflow, here is an example:

    ```yaml
    #...
    jobs:
      tests:
        name: Compilation Warnings
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v2 # checkout the repository first
          - uses: straw-hat-team/github-actions-workflows/elixir/compilation-warnings@master
            with:
              elixir-version: '1.11' # optional, fallback to use .tool-versions
              otp-version: '22.3' # optional, fallback to use .tool-versions
    ```

