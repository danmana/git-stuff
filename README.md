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
        fixup = commit --amend --no-edit
        cfg = config --global
		reword = commit --amend
		rw = commit --amend -m
        aliases = !git config --get-regexp 'alias.*' | cut -c 7- | sed "'s/^\\(\\S\\+\\)/\\x1b[1;36m\\1\\x1b[0m/'"
        ahead = !sh -c 'BR=$(git rev-parse --abbrev-ref HEAD) && git log origin/$BR..$BR --oneline'
		push-gerrit = !sh -c 'git push $(git config --get remote.origin.url) HEAD:refs/for/$(git rev-parse --abbrev-ref HEAD)'
		push-gerrit-one = !sh -c 'BR=$(git rev-parse --abbrev-ref HEAD) && REV=$(git log origin/$BR..$BR --pretty=format:%H | tail -1) && git push $(git config --get remote.origin.url) $REV:refs/for/$BR'
		pg = !sh -c 'git push-gerrit'
		pgo = !sh -c 'git push-gerrit-one'
		unadd = reset HEAD
[push]
        default = upstream
```
