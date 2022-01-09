# Git Set SHT Bot User

Set the `git` user for the repository using Straw Hat Team bot account. Use it
for committing and pushing to the repository using the bot account.

- [How-to Guides](#how-to-guides)

## How-to Guides

### Get Started

1. Make sure `actions/checkout` action is used before this action.
2. Add this action to your job in your workflow, here is an example:

    ```yml
    #...
    jobs:
      something:
        name: Do something with git
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v2 # checkout the repository first
          - uses: straw-hat-team/github-actions-workflows/git/set-sht-bot-user@master
    ```
