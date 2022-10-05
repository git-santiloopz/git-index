# Index
1. [Releases](releases.md)

### Resources
1. [Commit Message Imperative Style](https://chris.beams.io/posts/git-commit/#imperative)
1. [Commit Best Practises](https://medium.com/@nawarpianist/git-commit-best-practices-dab8d722de99)
1. [Autosquashing Git Commits](https://thoughtbot.com/blog/autosquashing-git-commits)
1. [Squash Commits Into One](https://www.internalpointers.com/post/squash-commits-into-one-git)
1. [Guide to Meaningful Commit Messages](https://medium.com/swlh/writing-better-commit-messages-9b0b6ff60c67)

### Glossary
* rebase
* interactive rebase

### Rebase
During an `interactive rebase` there are **two ways to combine commits** —`fixup` and `squash`— and there are two corresponding options for the `git-commit` command, conveniently called `--fixup` and `--squash`. These options instruct `Git` to **write a commit message for us**, expressing the intention that this new commit will eventually be `squashed` (or `fixed up`) with some existing commit.  

#### Correcting a typo example
```
$ git add .
$ git commit --fixup bbb2222
[my-feature-branch ddd4444] fixup! A second commit
```
After this `history` might look like this:
```
$ git log --oneline --decorate
ddd4444 (HEAD, my-feature-branch) fixup! A second commit
ccc3333 A third commit
bbb2222 A second commit
aaa1111 A first commit
9999999 (main) Old stuff on main
```
I’ve dealt with all of the feedback on my pull request, so I’m ready to `rebase`. To take full advantage of the `commit` message `git commit --fixup` generated for me, I need to pass the `--autosquash` option to `rebase` to tell Git to act the message:
```
git rebase --interactive --autosquash main
```
This is still an `interactive` rebase, so **Git will still open an editor session where I can manipulate the commits on our branch**, but the `--fixup` commit I made is already in the correct place in the list, and already marked with the correct action:
```
pick aaa1111 A first commit
pick bbb2222 A second commit
fixup ddd4444 fixup! A second commit
pick ccc3333 A third commit
```
