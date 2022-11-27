# ASDF Get Versions

Returns the versions from the .tool-versions file managed by asdf.

- [How-to Guides](#how-to-guides)

## Explanations

This action will return all the version from the .tool-versions file managed by
asdf as a JSON string where the key is the package name and the value is the
version.

## How-to Guides

### Get Started

1. Make sure `actions/checkout` action is used before this action.
2. Add this action to your job in your workflow, here is an example:

    ```yml
    #...
    jobs:
      something:
        name: Setup NodeJS
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v2 # checkout the repository first
          - uses: straw-hat-team/github-actions-workflows/asdf/git-versions@master
            id: asdf-versions
          - shell: sh
            run: |
              # Notice that the output is a JSON string
              echo ${{ fromJSON(steps.asdf-versions.outputs.versions).nodejs }}
    ```
