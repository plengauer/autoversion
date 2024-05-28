A Github action to automatically release new versions of your software. It automatically finds files containing version numbers for your software in this repo (not dependencies), feeds the commit messages since the last bump to an AI to determine how to increment the version, and then opens a PR.

Use it like this:
```yaml
name: Autoversion

on:
  workflow_dispatch:
  schedule:
    - cron: '0 0 * * 0' # TODO when to run

jobs:
  bump:
    runs-on: ubuntu-latest
    steps:
      - uses: plengauer/autoversion@main # TODO pin to a version if needed
        with:
          github_token: ${{ secrets.MY_GITHUB_TOKEN }} # token for GITHUB for the user to create the PR, needs repo write permissions
          openai_token: ${{ secrets.MY_OPENAI_TOKEN }} # token for OpenAI
```
