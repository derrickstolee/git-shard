A Time-Based Shard of the Git Repository
========================================

This repository is only an example of how one can shard a repository based on time.

The root commit of this repository shares a root tree with Git's `v2.37.0` tag. You can create a combined version of the history using these commands:

```ShellSession
$ git clone https://github.com/git/git git-old
$ git clone https://github.com/derrickstolee/git git-new

$ echo "$(pwd)/git-old/.git/objects >git-new/.git/objects/info/alternates
$ cd git-new

$ GIT_REPLACE_REF_BASE=refs/shard git replace \
                  b49d35c8288501462ca1a008b3bb2efb9b4c4a9d \
                  e4a4b31577c7419497ac30cebe30d755b97752c5

$ git log --oneline
b49d35c828 (HEAD -> main) new root commit

$ GIT_REPLACE_REF_BASE=refs/shard git log --oneline -n 5
b49d35c828 (HEAD -> main, replaced) Git 2.37
49c837424a Merge branch 'jc/revert-show-parent-info'
5dba4d6540 Merge tag 'l10n-2.37.0-rnd1' of https://github.com/git-l10n/git-po
fc0f8bcd64 revert: config documentation fixes
71e3a31e40 l10n: sv.po: Update Swedish translation (5367t0f0u)
```

License
-------

This repository is equivalent to [Git](https://github.com/git/git) at the `v2.37.0` tag, except for this `README.md` file. As such, this repository is available under the LGPL v2.1 public license. See `LGPL-2.1` for details.
