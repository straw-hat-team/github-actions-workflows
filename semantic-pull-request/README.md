# Semantic Pull Request

Ensures that the Pull Request title matches
the [Conventional Commits spec](https://www.conventionalcommits.org/en/v1.0.0/).

- [How-to Guides](#how-to-guides)

## How-to Guides

### Get Started

1. Add this action to your job in your workflow, here is an example:

    ```yml
    on:
      pull_request:
        types:
          - opened
          - edited
          - synchronize
    #...
    jobs:
      something:
        name: Do something with git
        runs-on: ubuntu-latest
        steps:
          - uses: straw-hat-team/github-actions-workflows/semantic-pull-request@master
    ```
