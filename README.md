# GIT

### Config
Get local and global config
```shell
git config --get --local <key> # i.e user.name
git config --get --global <key> # i.e user.name
```
Set local and global config
```shell
git config --local <key> "<value>" # i.e user.name
git config --global <key> "<value>" # i.e user.email
```

### List remote branches
```shell
git branch -a
```

### Tack remote branches
```shell
git checkout -b local-branch-name <remote-branch-to-track> # i.e origin/feature-whateva
```

### Do not track file permissions changes
```shell
git config core.fileMode false
```

what does it mean fast-forward vs no-ff vs squash?

cherry-pick a feature?