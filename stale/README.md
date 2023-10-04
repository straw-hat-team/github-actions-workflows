# Stale

Warns and then closes issues and PRs that have had no activity for a specified amount of time.

- [How-to Guides](#how-to-guides)

## How-to Guides

### Get Started

1. Add this action to your job in your workflow, here is an example:

    ```yml
    name: 'Close stale issues and PRs'

    on:
      workflow_dispatch:
      schedule:
        - cron: '30 1 * * *'
    
    permissions:
      contents: write
      issues: write
      pull-requests: write
   
    #...
   
    jobs:
      stale:
        runs-on: ubuntu-latest
        steps:
          - uses: straw-hat-team/github-actions-workflows/stale@master
    ```
