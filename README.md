# [`gh-xz`](https://github.com/hakadoriya/gh-xz)

`gh-xz` is a gh command e**X**tension for utilitie**Z**.

## CLI

```sh
# install
gh extension install https://github.com/hakadoriya/gh-xz

# usage
gh xz
```

## Usage

```console
$ gh xz
gh-xz - gh command eXtension to utilitieZ.

Usage:
  gh-xz <SUBCOMMAND>

SUBCOMMAND:
    pr-upsert-comment
        Upsert a comment that has a specific anchor string in a pull request.
        Usage:
          gh-xz pr-upsert-comment <OWNER/REPOSITORY> <PR_NUMBER> <ANCHOR_STRING> <COMMENT_NEW_BODY>
    help, usage
        Show this help message.
        Usage:
          gh-xz help
```
