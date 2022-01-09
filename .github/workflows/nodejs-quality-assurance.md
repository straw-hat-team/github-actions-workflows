# NodeJS Quality Assurance

Enables Quality Assurance tools:

- Testing (jest)
- Formatter (prettier)

## Usage

Make sure your `.tool-versions` exists and contains the `nodejs` version you want to use. It uses .tool-versions to set
up the NodeJS version.

Create a new GitHub Workflow (ex: `.github/workflows/ci.yml`) with the following content:

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
