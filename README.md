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

### `get-anchored-comment`

Get a comment that has a specific anchor string in a pull request.

```console
$ gh xz get-anchored-comment owner/repo 123 anchor1
This is a comment.

<!-- anchor1 -->
```

### `put-anchored-comment`

Put a comment that has a specific anchor string in a issue or pull request.

```console
$ gh xz put-anchored-comment owner/repo 123 anchor1 "This is a comment."

$ gh xz get-anchored-comment owner/repo 123 anchor1
This is a comment.

<!-- anchor1 -->

$ gh xz put-anchored-comment owner/repo 123 anchor1 "This is a new comment."

$ gh xz get-anchored-comment owner/repo 123 anchor1
This is a new comment.

<!-- anchor1 -->
```

## Usage

```console
$ gh xz
gh-xz - gh command eXtension to utilitieZ.

Usage:
  gh-xz <SUBCOMMAND>

SUBCOMMAND:
    get-anchored-comment
        Get a comment that has a specific anchor string in a issue or pull request.
        Usage:
          gh-xz get-anchored-comment <OWNER/REPOSITORY> <PR_NUMBER> <ANCHOR_STRING>
        e.g.:
          gh-xz get-anchored-comment owner/repo 123 "anchor"
    put-anchored-comment
        Put a comment that has a specific anchor string in a issue or pull request.
        Usage:
          gh-xz put-anchored-comment <OWNER/REPOSITORY> <PR_NUMBER> <ANCHOR_STRING> <COMMENT_NEW_BODY_CONTENT|COMMENT_NEW_BODY_FILE>
        e.g.:
          gh-xz put-anchored-comment owner/repo 123 "anchor" "This is a new comment."
          gh-xz put-anchored-comment owner/repo 123 "anchor" @./comment.md
          cat ./comment.md | gh-xz put-anchored-comment owner/repo 123 "anchor" @-
    help, usage
        Show this help message.
        Usage:
          gh-xz help
```

## GitHub Actions

[`hakadoriya-actions/setup-gh-xz`](https://github.com/hakadoriya-actions/setup-gh-xz) is a GitHub Actions to install `gh-xz` in GitHub Actions.

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
          gh xz put-anchored-comment ${{ github.repository }} ${{ github.event.number }} anchor1 "This comment is posted by gh-xz."
```
