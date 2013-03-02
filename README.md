git-stuff
=========

Various git configurations

```INI
[alias]
        co = checkout
        br = branch
        pr = pull --rebase
        st = status
        cm = commit -m
        cfg = config --global
		reword = commit --amend
		rw = commit --amend -m
        aliases = !git config --get-regexp 'alias.*' | cut -c 7- | sed "'s/^\\(\\S\\+\\)/\\x1b[1;36m\\1\\x1b[0m/'"
        ahead = !sh -c 'BR=$(git rev-parse --abbrev-ref HEAD) && git log origin/$BR..$BR --oneline'
[push]
        default = upstream
```
