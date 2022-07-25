git-stuff
=========

Various git configurations

```INI
[core]
    editor = 'C:/Program Files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin
[user]
        name = Dan Manastireanu
        email = 498419+danmana@users.noreply.github.com
        signingkey = 4ADB6ED298D5380B
[commit]
        gpgsign = true
[alias]
        co = checkout
        br = branch
        pr = pull --rebase
        st = status
        cm = commit -m
        fixup = commit --amend --no-edit
        cfg = config --global
        reword = commit --amend
        rw = commit --amend -m
        aliases = !git config --get-regexp 'alias.*' | cut -c 7- | sed "'s/^\\(\\S\\+\\)/\\x1b[1;36m\\1\\x1b[0m/'"
        ahead = !sh -c 'BR=$(git rev-parse --abbrev-ref HEAD) && git log origin/$BR..$BR --oneline'
        push-upstream = !sh -c 'git push --set-upstream origin $(git rev-parse --abbrev-ref HEAD)'
        pushu = !sh -c 'git push-upstream'
        prune-branches = !git remote prune origin && git branch -vv | grep ': gone]' | awk '{print $1}' | xargs -r git branch -D
        pbr = prune-branches
        prune-tags = !git tag -l | xargs git tag -d --quiet && git fetch -t
        pt = prune-tags
        fix-tags-dev = !git prune-tags && git push --delete origin $(git tag -l "dev-build-number-*" | sort -t '-' -k 3 -n -r | tail -n +2)
        fix-tags-staging = !git prune-tags && echo git push --delete origin $(git tag -l "staging-build-number-*" | sort -t '-' -k 3 -n -r | tail -n +2)
        fix-tags-production = !git prune-tags && echo git push --delete origin $(git tag -l "production-build-number-*" | sort -t '-' -k 3 -n -r | tail -n +2)
        update-fork = !sh -c 'git fetch upstream && git checkout master && git merge upstream/master'
        sync-fork = update-fork
        uf = update-fork
        find-merge = "!sh -c 'commit=$0 && branch=${1:-HEAD} && (git rev-list $commit..$branch --ancestry-path | cat -n; git rev-list $commit..$branch --first-parent | cat -n) | sort -k2 -s | uniq -f1 -d | sort -n | tail -1 | cut -f2'"
        show-merge = "!sh -c 'merge=$(git find-merge $0 $1) && [ -n \"$merge\" ] && git show $merge'"
        unadd = reset HEAD
[gpg]
        program = /opt/homebrew/bin/gpg
[push]
        default = upstream
[diff]
        tool = kdiff3
        guitool = kdiff3
[merge]
        tool = kdiff3
```
