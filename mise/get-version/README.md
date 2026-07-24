# Mise Get Version

Returns the version of the tool from mise.toml file managed by mise.

- [How-to Guides](#how-to-guides)

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
          - uses: straw-hat-team/github-actions-workflows/mise/get-version@master
            id: nodejs-version
            with:
              plugin-name: nodejs
          - shell: sh
            run: |
              echo ${{ steps.nodejs-version.outputs.plugin-version }}
    ```
