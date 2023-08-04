## Commit Messages
1) Modifying Modules Specs or Behavior:
- `BRK`: (Break) When a functionality is broken on purpose
- `CHG`: (Change) Changes to module's specifications 
- `UPD`: (Update) When a change in interface is required 
- `FIX`: (Bug Fix) Correction to behavior, to make it compliant with specs
- `TUN`: (Tuning) Tuning of algorithm, either parameters settings or code changes
- `NEW`: (New) Strict addition of services, new functionality that is compatible with the current version

2) Not Modifying Modules Feature Behavior:
- `RPT`: (Reports) Changes to reporting
- `DOC`: (External Documentation) Changes to external documentation
- `LOG`: (Logging) Changes to logging
- `RFG`: (Refactoring) Stric reimplementation of a given specification, no change in behavior
- `TST`: (TEST) Any change in automated tests. Only used in repos where code and automated tests coexist
- `DEV`: (Development Tools) Changes to internal documentation (including comments in code) or debugging tools
- `SPC`: (Spacing) Changes to code spacing or general presentation; no change in the code that is executed.

## Aliases
```
$ gco // git checkout
$ gci // git commit
$ gst // git status
$ gupd // git update
$ gf // git fetch
$ gdi // git diff
```

## Symbols
```
$ * // uncommitted changes
$ % // untracked in git
```

## Tags
- A tag is used to label and mark a specific commit in the history. It is usually used to mark release points (eg. v1.0, etc.)
- Although a tag may appear similar to a branch, a tag, however, does not change. It points directly to a specific commit in the history and will not change unless explicitly updated
```
$ git fetch --tags // --tags will fetch all tags as well
$ git tag // list all tags
$ git tag --list 'v-*' // list all tags with given pattern ex: v-
$ git checkout tags/<tag_name> -b <branch_name> // check out the tag 
$ git tag -d <tag_name> // delete local †ag
$ git push --delete origin <tag name> // Delete a tag from the server with push tags
$ git push --tags // Push all tags
```

## Fetch
```
$ git fetch --all // --all will fetch all the remotes
```

## gitk
```
$ gitk --all
$ git gui
```

## Checkout
```
$ git checkout - // checkouts last branch
$ git checkout -b <branch_name> // checkout into new branch
$ gco HEAD~ // go back one commit
```

## Rebase
- Golden rule of Rebase:
“No one shall rebase a shared branch” — Everyone about rebase
```
$ git rebase -i <target_branch> // rebase current branch into the target branch
$ git rebase --help
$ git pull --rebase
```

## Merge
```
$ git merge --help
$ git merge --abort // deal with merge conflicts
```

## Last Commit Message
```
$ git commit --amend // change last commit message
```

## Reset
```
$ git reset HEAD@{index} // number of commits back
```

## Delete
```
$ git branch --delete <branchname>
$ git branch --unset-upstream
```

## Stash
```
$ git stash 
$ git stash pop 
```

## Cherry Pick
```
$ git cherry-pick <commit_reference>
$ git cherry-pick --abort // stop cherry picking
```

## Log
```
$ git log // prints committed or uncommitted messages
$ git log -2 // last two commits
$ git reflog // list of everyhing you've done in git
$ git for-each-ref --sort=-committerdate --format='%(refname:short) - %(authorname) - %(committerdate:short)' refs/remotes/ 
```

## Difference
```
$ git diff <revision> <filename> // shows differences in a file between snapshots
$ git diff <filename>: show changes you made relative to the staging area
```

## Blame
```
$ git blame welcome.txt // tells you who changed each line, and when
$ git blame -L 1,2 welcome.txt
$ git blame -L 1, +4 welcome.txt // 4 lines after line 1
```

## Revert
```
$ git revert --abort
$ git revert --continue
```

## Commit Email
```
1. Click on commit link
2. Add `.patch` to the end of the link of the commit message
```
