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

### `pr-get-annotated-comment`

Get a comment that has a specific annotation string in a pull request.

```console
$ gh xz pr-get-annotated-comment owner/repo 123 annotation1
This is a comment.

<!-- annotation1 -->
```

### `pr-upsert-annotated-comment`

Upsert a comment that has a specific annotation string in a pull request.

```console
$ gh xz pr-upsert-annotated-comment owner/repo 123 annotation1 "This is a new comment."

$ gh xz pr-get-annotated-comment owner/repo 123 annotation1
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
    pr-get-annotated-comment
        Get a comment that has a specific annotation string in a pull request.
        Usage:
          gh-xz pr-get-annotated-comment <OWNER/REPOSITORY> <PR_NUMBER> <ANCHOR_STRING>
        e.g.:
          gh-xz pr-get-annotated-comment owner/repo 123 "annotation"
    pr-upsert-annotated-comment
        Upsert a comment that has a specific annotation string in a pull request.
        Usage:
          gh-xz pr-upsert-annotated-comment <OWNER/REPOSITORY> <PR_NUMBER> <ANCHOR_STRING> <COMMENT_NEW_BODY_CONTENT|COMMENT_NEW_BODY_FILE>
        e.g.:
          gh-xz pr-upsert-annotated-comment owner/repo 123 "annotation" "This is a new comment."
          gh-xz pr-upsert-annotated-comment owner/repo 123 "annotation" @./comment.md
          cat ./comment.md | gh-xz pr-upsert-annotated-comment owner/repo 123 "annotation" @-
    help, usage
        Show this help message.
        Usage:
          gh-xz help
```
