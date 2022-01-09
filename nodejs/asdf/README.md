# NodeJS ASDF

Set the `Node.js` version using the `.tool-versions` file managed by [asdf](https://asdf-vm.com/).

- [How-to Guides](#how-to-guides)

## How-to Guides

### Get Started

1. Add the job to your workflow:

```yml
#...
jobs:
  something:
    name: Setup NodeJS
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2 # checkout the repository first
      - uses: straw-hat-team/github-actions-workflows/nodejs/asdf@master
```
