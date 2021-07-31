# git_hooks

test usage of git hooks

## Requirements

`git` and `ssh` access to "remote" host.

## Procedure

1. Create a remote bare repo.
1. Add hooks on remote
1. push to remote

```text
cd ~/Downloads/
mkdir git_hooks
cd git_hooks
git init --bare
cd hooks
```

```text
hbarta@olive:~/Downloads/git_hooks/hooks$ cat update
#!/bin/sh
#

echo "git update hook executed" >/tmp/update.txt

exit 0
hbarta@olive:~/Downloads/git_hooks/hooks$ cat post-update
#!/bin/sh
#

echo "post-update hook executed" >> /tmp/post-update.txt
hbarta@olive:~/Downloads/git_hooks/hooks$ 
```

```text
git remote add olive ssh://hbarta@olive:/home/hbarta/Downloads/git_hooks
```

This works as desired. Now try with remote on Raspberry Pi (the intended target.)

```text
git remote add prelude ssh://hbarta@prelude:/home/hbarta/Downloads/git_hooks
```

This works. Also need to add the following to push to prelude by deraulkt (e.g. `git push` pushes to all three remotes.)

```text
git remote set-url --add --push origin  ssh://hbarta@prelude:/home/hbarta/MyDocs//my-notes
```
