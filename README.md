# forge-previewer-action

> **Warning**
> This action is still a work-in-progress and not ready for use.

This is a GitHub Action that makes adding the [forge-previewer](https://github.com/ryangjchandler/forge-previewer) easier to integrate in your workflows.

## Usage

This action is best used in actions that run when a pull request is opened and closed. This is not a requirement but is the intended usage scenario.

The following is an example workflow (almost) ready to be used.

```yml
name: "Build preview environment"

on:
    pull_request:
        types: [opened]

jobs:
    preview:
        runs-on: ubuntu-latest

        steps:
            - name: Checkout code
              uses: actions/checkout@v2
            
            - name: Run forge-previewer
              uses: ryangjchandler/forge-previewer-action@v1
              with:
                forge-token: ${{ secrets.FORGE_TOKEN }}
                server-id: ${{ secrets.FORGE_SERVER_ID }}
                domain: ${{ secrets.FORGE_DOMAIN }}
                branch: ${{ github.head_ref }}
                repo: 'my-org/my-repo'
```