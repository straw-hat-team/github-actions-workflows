# NodeJS Setup

Set up NodeJS, use `.tool-versions` file as a fallback for the version.

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
          - uses: straw-hat-team/github-actions-workflows/nodejs/setup@master
            with:
              nodejs-version: 12.x # optional, fallback to use .tool-versions  
    ```
