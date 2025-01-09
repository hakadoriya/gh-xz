# [`gh-xz`](https://github.com/hakadoriya/gh-xz)

`gh-xz` is a gh command e**X**tension for utilitie**Z**.

## Installation

```sh
# install
gh extension install https://github.com/hakadoriya/gh-xz

# now you can use `gh xz`
gh xz
```

## Features

### `get-annotated-comment`

Get a comment that has a specific annotation string in a pull request.

```console
$ gh xz get-annotated-comment owner/repo 123 annotation1
This is a comment.

<!-- annotation1 -->
```

### `put-annotated-comment`

Put a comment that has a specific annotation string in a issue or pull request.

```console
$ gh xz get-annotated-comment owner/repo 123 annotation1
This is a comment.

<!-- annotation1 -->

$ gh xz put-annotated-comment owner/repo 123 annotation1 "This is a new comment."

$ gh xz get-annotated-comment owner/repo 123 annotation1
This is a new comment.

<!-- annotation1 -->
```

## Usage

```console
$ gh xz
gh-xz - gh command eXtension to utilitieZ.

Usage:
  gh-xz <SUBCOMMAND>

SUBCOMMAND:
    get-annotated-comment
        Get a comment that has a specific annotation string in a issue or pull request.
        Usage:
          gh-xz get-annotated-comment <OWNER/REPOSITORY> <PR_NUMBER> <ANCHOR_STRING>
        e.g.:
          gh-xz get-annotated-comment owner/repo 123 "annotation"
    put-annotated-comment
        Put a comment that has a specific annotation string in a issue or pull request.
        Usage:
          gh-xz put-annotated-comment <OWNER/REPOSITORY> <PR_NUMBER> <ANCHOR_STRING> <COMMENT_NEW_BODY_CONTENT|COMMENT_NEW_BODY_FILE>
        e.g.:
          gh-xz put-annotated-comment owner/repo 123 "annotation" "This is a new comment."
          gh-xz put-annotated-comment owner/repo 123 "annotation" @./comment.md
          cat ./comment.md | gh-xz put-annotated-comment owner/repo 123 "annotation" @-
    help, usage
        Show this help message.
        Usage:
          gh-xz help
```

## GitHub Actions

`hakadoriya-actions/setup-gh-xz` is a GitHub Actions to install `gh-xz` in GitHub Actions.

### Example

```yaml
name: example

on:
  pull_request:

jobs:
  example:
    if: github.actor != 'dependabot[bot]' && github.actor != 'renovate[bot]'
    runs-on: ubuntu-latest
    permissions:
      contents: read
      pull-requests: write
    steps:
      - uses: hakadoriya-actions/setup-gh-xz@v0.0.1
      - name: Run gh xz
        env:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        shell: bash
        run: |
          gh xz put-annotated-comment ${{ github.repository }} ${{ github.event.number }} annotation1 "This comment is posted by gh-xz."
```
