# Git

<!-- vim-markdown-toc GFM -->
* [Tips](#tips)
    * [Discard local commits and reset to master](#discard-local-commits-and-reset-to-master)

<!-- vim-markdown-toc -->

## Tips

### Enable credentials caching

```bash
git config --global credential.helper cache
```

### Discard local commits and reset to master

```bash
git reset --hard origin/master
```
