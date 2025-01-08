# gh-pr-update-comment

## CLI

```sh
gh-pr-update-comment \
  user/repo \
  123 \
  "<!-- anchor -->" \
  "new body\n\n<!-- anchor -->"
```

## GitHub Actions

A workflow to update a comment in a pull request.

## example

```yml
name: example

on:
  pull_request:

jobs:
  gh-pr-update-comment:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      pull-requests: write
    steps:
      - uses: hakadoriya-actions/gh-pr-update-comment@v0.0.1
        id: gh-pr-update-comment
        with:
          repo: user/repo
          pr-number: 123
          comment-anchor-string: "<!-- anchor -->"
          comment-new-body: "new body\n\n<!-- anchor -->"
          debug: true
```
