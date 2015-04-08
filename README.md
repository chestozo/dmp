# dmp
Diff tool based on [google-diff-match-patch](http://code.google.com/p/google-diff-match-patch/).
You have to have node.js installed in order to `dmp` to work.

The main motivation to write this tool was to see letter specific diff
for unicode symbols (cyrillic letters in particular).

Now it is possible:

![](https://s3.amazonaws.com/f.cl.ly/items/3l0k1E2305132p103X1y/Screen%20Shot%202015-04-08%20at%2020.19.34.png).

## git integration
Edit your .gitconfig like so:
```
[pager]
    difftool = true
[diff]
    tool = dmp
[difftool "dmp"]
    cmd = ~/path/to/dmp \"$LOCAL\" \"$REMOTE\"
[alias]
    dd = difftool
    dc = difftool --cached
    sh = !"sh() { local c="$1"; c=${c:=HEAD}; git difftool $c~..$c; }; sh"
```

See letter specific diff with this git commands:
```sh
git dd # git diff --color-words=. analog
git dc # git diff --cached --color-words=. analog
git sh # git show --color-words=. analog
```
