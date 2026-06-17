---
mocs:
    - "[[public-notes/03-resources/tools.moc.md|Tools & Environment]]"
tags:
    - dev/tools
---

+ **Version Control?**: controlling, organizing, and tracking different versions in history of computer files
+ Distribute Version Control System
---
**Resources**
+ Pro Git (book)
![[Pasted image 20250117144935.png]]
## Difference between others VCSs
+ Git is no delta based VCS, instead it saves a stream of snapshots, if files has not changed it reference the file in the snapshot where it was last changed
![[Pasted image 20250117152951.png]]
+ checksumming: SHA-1 calculated based on the content of a file or directory, git uses it to ensure data integrity in its db
+ Then almost everything is undoable
+ nearly all operation is local -> More speed in contrast with VCSs
# 1. Install and git Config
```
git config --global user.name "John Doe"  
git config --global user.email johndoe@example.com
git config --global core.editor emacs
git config --global init.defaultBranch main
git config --global credential.helper cache # don't type your password every time

git help <verb>  
git <verb> --help
man git-<verb>
# use -h instead of --help to more conscice output
```
# 2. The Three States (Workflow)
+ Git has 3 main states for files: modified, staged, committed.|

## Modified:
- A file is in the modified state when you have changed it in your working directory but have not yet staged it for a commit.
- This means the changes are only in your working directory and are not yet part of the version history.
- Example: You edit a file `example.txt` to fix a bug or add a new feature.
## Staged:
- A file is in the staged state when you have marked it to be included in the next commit.
- Staging a file means it is added to the staging area (also known as the index).
- Example: You use the command `git add example.txt` to stage your changes.
## Committed
- A file is in the committed state when it has been saved in the local repository.
- Committing a file means your changes are recorded in the repository’s history.
- Example: You use the command `git commit -m "Fix bug in example.txt"` to commit your staged changes.
---
![[Pasted image 20250118162734.png]]

# Fundamental Git Commands
```
git status # -s for short output
git add # track new files and stage currently tracked files and marking merge-conflicted files as resolved

git diff # changes that you have made but not staged: compares your working directory with your staging area
git diff --staged # what is in your staging area with your last commit

git commit -m ""
git commit -am "" # skip git add (Inlcude all changed files)

git rm <path> # remove file from working directory and staging area
git rm -f # the same but if the file was already committed

git rm --cached # only removed from staging area
git mv <name1> <name2> # rename, untrack prev file and stage new file

git log # commit history, also has powerful options / flags to filter commit history
git log --no-merges
```
+ git add: can be summarized as "add precisely this content to the next commit"

## Undoing Things

> [!WARNING]
> If you do it wrong you can lose work

### Redo last local commit
```
git commit --amend # takes your staging area and use it for commit
```

### Unstaging Staged file
it moves the changes from the staging area back to the working directory, making them appear as modified but not staged.

```
git reset HEAD <file_pattern_glob>
```

Or with the new command `git restore`
```
$ git restore <file> # This restores the specified file(s) to the state of the latest commit

$ git restore --staged <file> # This command will unstage `file`, moving it from the staging area back to the working directory.
```

### Discard Changes
```
git checkout -- <file name>
```
+ any local changes you have made are gone
+ git just replaced that file with the last staged or committed version
## Working with remotes
```
$ git remote -v
$ git remote add <shortname> <url> # add new remote to git repo
$ git remote show <remote>
$ git remote rename <prev name> <new name>
$ git remote remove <remote>
```

### fetch
+ updates your local copies of the remote branches without merging them into your current branch.
+ only updates the remote-tracking branches, it is a safe operation that does not affect your working directory or branch. You can review the incoming changes before deciding to merge or rebase them.
```
git fetch
git fetch <remote-name>
```
+ You can review the fetched changes using commands like:
```
git log origin/main
git diff origin/main
```

### pull
+ Automatically fetch and merge a remote branch into local branch
### push
```
$ git push <origin> <branch>
```

## Tagging
+ mark important commits such as releases, etc
```
$ git tag # list your tags
```

### Creating Tags
+ Git supports two types of tags:
	1. **lightweight**: is just a pointer to an specific commit
	2. **annotated**:  are stored full objects in the git database: checksummed, tagger name, email, date, can be signed and verified with GPG

```
$ git tag -a v1.4 -m "my version 1.4" # create annotated tag
$ git show v1.4 # display info of annotated tag
$ git tag v1.4-lw # don't supply any of the -a, -s or -m options, just tag name
$ git tag -d <tagname> # remove tag name
```

#### Push tags
`git push` by default don't transfer tags to remote servers, you will have to explicity push tags:

```
git push origin <tagname>
git push --tags # push all tags
git push origin --delete <tagname>
```

#### Checking out tags
view versions of the files a tag is pointing to

> [!NOTE]
> You will enter detached HEAD state

```
$ git checkout <tagname>
```


# Git Aliases
Common aliases
```
$ git config --global alias.unstage 'reset HEAD --'
$ git config --global alias.last 'log -1 HEAD'
```


# Git Branching
+ The "killer feature" of git
+ `HEAD` Pointer to local branch you're currently on (last commit)
```
$ git branch <name> #create new branch
$ git checkout <branch> # switch branch
$ git checkout -b <name> # create a new branch a move to it
$ git branch -d <name> # delete unused branch
$ git branch # list branches
$ git branch --merged # branches contain work you have merged or --no-merged to do the opposite
```

```
$ git log <branch name> # show commit history to specific branch
$ git log --all # show all branches
$ git log --oneline --decorate --graph --all
```

### Git Switch
+ Newly introduced is recommended to use instread `git checkout` for branch operations
```
git switch <name> # switch to existing branch
git switch -c <name> # create and switch to new branch
git switch - # return to you previously checkout branch
```

### Git merge
check out the branch you wish to merge  into and then run `git merge`

```
git switch main
git merge hotfix/blabla
```

Git merge will use one of two strategies
1. **Fast Forward**: If the current branch has not diverged from the branch being merged, Git performs a fast-forward merge
	+ This simply moves the current branch pointer forward to the latest commit on the other branch.
![[Pasted image 20250120153707.png]]
![[Pasted image 20250120153721.png]]
1. **Three-Way Merge**: - If the branches have diverged, Git performs a three-way merge.
	+ This involves creating a new commit that combines the changes from both branches.
![[Pasted image 20250120153325.png]]
![[Pasted image 20250120153335.png]]
#### Conflicts
+ If there are conflicting changes in the two branches, Git will prompt you to resolve the conflicts manually.
- After resolving the conflicts, you need to stage the resolved files and complete the merge.

### Tracking Branches
Tracking branches in Git are local branches that track the state of remote branches.
```
$ git checkout -b feature-branch origin/feature-branch
$ git branch --set-upstream-to=origin/feature-branch feature-branch
$ git branch -vv # list tracked branches
```
### Deleting Remote Branches
```
$ git push origin --delete <branch name>
```

### Rebasing
In git are two main ways to integrate chagnes from one branch into another: 1. merge 2. rebase.
+ rebase give us cleaner commit history (linear history)
+ never rebase something that you have pushed
#### Basic Rebasing
+ `rebase`: You can take all the changes that were committed on one branch and reapply them in a different branch. e.g.
![[Pasted image 20250120145903.png]]

#### --onto option ??
```
$ git checkout experiment
$ git rebase main
```
then
![[Pasted image 20250120145921.png]]

---
Also:
+ Three way merge (divergent branches) this creates a new merge commit
+ vs fast forwared
# Git Vocab
- **Working Directory**: This is the directory on your filesystem where the files of your project are located.
- **Working Tree**: This term refers to the set of files in your working directory that are being tracked by Git. It represents the current state of the files checked out from the repository, including any modifications that have not yet been committed.
- **Snapshot**: Is a record of the state of the project, each commit represents an snapshot
- **Repository**: is a data structure used by git to store metadata (commit history, branches, etc.) and the of files and directories.
- **untracked files**: Each file in your working directory that were not in your previous snapshot as well as newly staged files.