# NodeJS Quality Assurance

Enables Quality Assurance Actions for NodeJS projects.

- [How-to Guides](#how-to-guides)
- [Explanations](#explanations)

## Explanations

This workflow is a suit of development tool setup for NodeJS that leverage other actions such as:

- [nodejs/prettier](../../nodejs/prettier/README.md) for code formatting.
- [nodejs/jest](../../nodejs/jest/README.md) for testing.

You can disable these actions by changing the setting the workflow. Please check the workflow input documentation.

## How-to Guides

### Get Started

1. Make sure your `.tool-versions` exists and contains the `nodejs` version you want to use. It uses .tool-versions to
   set up the NodeJS version.

2. Create a new GitHub Workflow (ex: `.github/workflows/ci.yml`) if you don't have one already.
3. Add the following this workflow to your workflow, here is a final example:

```yaml
name: NodeJS Quality Assurance

on:
  push:
    branches:
      - master
  pull_request:
    branches:
      - master

jobs:
  nodejs-quality-assurance:
    uses: straw-hat-team/github-actions-workflows/.github/workflows/nodejs-quality-assurance.yml@master
    with:
      jest-enabled: true
      prettier-enabled: true
```
