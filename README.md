# [`gh-exz`](https://github.com/hakadoriya/gh-exz)

`gh-exz` is a gh command extension to utilities.

## CLI

```sh
# install
gh extension install https://github.com/hakadoriya/gh-exz

# usage
gh exz
```

## Usage

```console
$ gh exz
gh-exz - Update a comment that has a specific anchor string in a pull request.

Usage:
  gh-exz <SUBCOMMAND>

SUBCOMMAND:
    pr-upsert-comment
        Upsert a comment that has a specific anchor string in a pull request.
        Usage:
          gh-exz pr-upsert-comment <OWNER/REPOSITORY> <PR_NUMBER> <ANCHOR_STRING> <COMMENT_NEW_BODY>
    install
        Install this extension.
        Usage:
          gh-exz install
    self-update
        Update this script itself.
        Usage:
          gh-exz self-update
    help, usage
        Show this help message.
        Usage:
          gh-exz help
```
