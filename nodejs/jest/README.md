# NodeJS Jest

Runs [jest](https://jestjs.io/) testing.

- [How-to Guides](#how-to-guides)

## How-to Guides

### Get Started

1. Add the job to your workflow:

```yml
#...
jobs:
  check-format:
    name: Check Format
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2 # checkout the repository first
      - uses: straw-hat-team/github-actions-workflows/nodejs/jest@master
```
