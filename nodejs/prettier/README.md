# NodeJS Prettier

Runs [prettier](https://prettier.io/) on your code to check for formatting
errors.

- [How-to Guides](#how-to-guides)

## How-to Guides

### Get Started

1. Make sure `actions/checkout` action is used before this action.
2. Add this action to your job in your workflow, here is an example:

```yml
#...
jobs:
  check-format:
    name: Check Format
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2 # checkout the repository first
      - uses: straw-hat-team/github-actions-workflows/nodejs/prettier@master
```
