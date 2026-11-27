# herdr-core — hurt fork

A fork of [herdrdev/herdr-core](https://github.com/herdrdev/herdr-core), on top of upstream
`master` at `2e8043a`.

Branches:

- `hurt` (default) is upstream plus our changes. This is the one you want.
- `master` holds only upstream's commits, so syncing stays a fast-forward. It is not always
  current: compare it with upstream before relying on it.

## What's different from upstream

Nothing in the code yet: `hurt` is upstream plus this file.

## Build and install (macOS)

```sh
git checkout hurt
just install
hc --version
```

`just install` builds the `Herdr Core.app` bundle and links `hc` and `herdr-core` into
`~/.local/bin`. A running server keeps the build it was started with until it is restarted.

## Following upstream

```sh
git fetch upstream
git checkout master && git merge --ff-only upstream/master && git push origin master
git checkout hurt && git branch hurt-pre-$(date +%y%m%d) && git rebase master
git push origin hurt-pre-$(date +%y%m%d)
git push --force-with-lease origin hurt
```

The pre-rebase branch is pushed first, so the history before the rebase exists somewhere besides
one machine. Then build and install as above.
