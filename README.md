# [`gh-pr-update-comment`](https://github.com/hakadoriya/gh-pr-update-comment)

`gh-pr-update-comment` is a CLI tool to update a comment that has a specific anchor string in a pull request.

## CLI

```sh
gh-pr-update-comment \
  user/repo \
  123 \
  '<!-- anchor -->' \
  'new body <!-- anchor -->'
```

## GitHub Actions

A workflow for gh-pr-update-comment.

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
          comment-new-body: "new body <!-- anchor -->"
          debug: true
```
