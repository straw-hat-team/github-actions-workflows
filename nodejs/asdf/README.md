# NodeJS ASDF

Set the `Node.js` version using the `.tool-versions` file managed by [asdf](https://asdf-vm.com/).

- [How-to Guides](#how-to-guides)

## How-to Guides

### Get Started

1. Make sure `actions/checkout` action is used before this action.
2. Add the action to your job in your workflow, here is a final example:

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
