#Git Basics
##What is Git
- Distributed Version Control System (DVCS) as opposed to a central repository
- Official site: [git-scm.com](https://git-scm.com/)

## Command Line
```$ git help```

```$ git help [command]```

```$ git help config```

##Setting Up Git
```$ git config --global user.name &quot;BluePawDev&quot;```

```$ git config --global user.email jaruby@me.com```

```$ git config --global color.ui true```

##Starting a Repo

Creates local repo directory

```$ cd documents```

```$ cd development```

```$ mkdir sandbox-git```

```$ cd sandbox-git```

```$ git init```

##Workflow
Create it (i.e. files) -&gt; stage it -&gt; commit it

###Command Line
To check what&#39;s changed since last commit

```$ git status```

```$ git add README.md```

README.md is now staged

###To commit:

```$ git commit -m &quot;Create a README&quot;```

###Adding Multiple Files to Staging

```$ git add README.md LICENSE```

_OR_

```$ git add --all```

Adds all new or modified files

To commit:

```$ git commit -m &quot;Add LICENSE and finish README&quot;```

##Git Timeline History

```$ git log```

NOTE: good practice to make commit notes in present tense opposed to past tense (e.g. &quot;create&quot; v. &quot;created&quot;)—think about what the commit does

##Different Ways to Add

- List of files ```$ git add <list of files>```

- All files ```$ git add --all```

- All .txt files in current directory ```$ git add *.txt```

- All .txt files in docs directory ```$ git add docs/*.txt```

- All files in docs directory ```$ git add docs/```

- All .txt files in entire project ```$ git add "*.txt"```

## Git Diff

Shows unstaged differences since last commit

$ git diff

Shows staged differences since last commit

$ git diff –staged

#Staging and Remotes

##Unstaging Files

(use &quot;git reset HEAD &lt;file&gt;...&quot; to unstage)

```$ git reset HEAD LICENSE```

This will unstage only the LICENSE file

HEADrefers to the last commit on the current branch (timeline) that we are on

```$ git reset HEAD```

This will unstage all files

## Discarding Changes

This will blow away all changes since last commit

```$ git checkout -- <file name>```

```$ git checkout -- LICENSE```

## Skip Staging and Commit

```$ git commit –a –m "Modify LICENSE"```

This will add changes from all tracked files and commit them

NOTE: will not add any newly created (e.g. untracked) files

## Undoing a Commit

**NOTE: do not perform after a**  **push**

```$ git reset --soft HEAD^```

This will undo the last commit and move everything from that commit back into staging

HEAD^instructs to move to the commit one before the current HEAD

## Adding (Amend) to a Commit

If you forgot to add a file…?

**NOTE: do not perform after a**  **push**

```$ git add <file name>```

```$ git add todo.txt```

```$ git commit --amend –m "Modify README.md and add todo.txt"```

Whatever has been staged will be amended to the last commit.

NOTE: this --amendcommit message will overwrite the previous commit message.

## Blow Away Last Commit

**NOTE: do not perform after a**  **push**

This will undo the last commit and all changes

$ git reset --hard HEAD^

This will undo the last **two** commits and all changes

$ git reset --hard HEAD^^

## Sharing: Push and Pull

Git does not take care of access control—to do so requires additional software

Hosted solutions (e.g. GitHub, BitBucket) can take of access control

**Or**

Gitosis or Gitorious will allow for self-managing access

### Adding a Remote

$ git remote add &lt;name&gt; &lt;address&gt;

$ git remote add origin https://github.com/BluePawDev/sandbox-git.git

&quot;origin&quot;is our (local) name for the remote repo—this can be any name you chose

### Removing a Remote

$ git remote rm &lt;name&gt;

$ git remote add origin

### List Remote Repos that Local Repo Know About

$ git remote -v

### Pushing to Remote

$ git push –u &lt;name&gt; &lt;branch&gt;

$ git push –u origin master

originspecifics the remote repository name (as it is known locally)

masterspecifics the local branch to push—usually master

#### Password Caching

[https://help.github.com/articles/set-up-git](https://help.github.com/articles/set-up-git)

### Pulling from Remote

$ git pull

Do this when you know others have made changes—you&#39;re not the only one working on the project—and you want to get their changes.

**Note: do this often**

This will pull down the changes and sync the local repo

## Having Multiple Remotes

May have multiple remotes (e.g. origin, test, production, etc.)

## Heroku Remote

Requires a Heroku account and Heroku gem installed

# Cloning and Branching

## Clone a Repo

$ git clone https://github.com/BluePawDev/sandbox-git.git

This will create a local directory with the repo&#39;s name

$ git clone https://github.com/BluePawDev/sandbox-git.git **git-demo**

This will create a local directory with the name of git-demo containing the sandbox-gitrepo

Both of these will accomplish three steps:

1. Downloads the entire repo to the local directory
2. Adds the riginremote and point riginto the clone URL
  1. This can be checked/verified by: $ git remote –v
3. Checks out initial branch (likely master)

## List Remotes

```$ git remote –v```

The –v requests verbose output

## Create a Branch

Need to work on a feature that will take some time?

Create a branch:

$ git branch cat

This only creates the branch—it does not switch to the newly created branch

Running $ git branchwill show:

cat

\*master

The \* indicates current branch we are on—or where our HEADis currently

## Switch to a Branch

To move to the branch:

$ git checkout cat

This will switch us to the cat timeline and HEADis now on cat

Rhyddid:sandbox-git Jason$ ls

LICENSE                README.md        cat.txt

Rhyddid:sandbox-git Jason$ git checkout master

Switched to branch &#39;master&#39;

Your branch is up-to-date with &#39;origin/master&#39;.

Rhyddid:sandbox-git Jason$ git branch

  cat

\* master

Rhyddid:sandbox-git Jason$ ls

LICENSE                README.md

## Combine (Merge) Branch I

$ git merge cat

This merges the catbranch with the masterbranch

### Branch Clean Up (Delete)

$ git branch -d cat

This deletes the catbranch

## Combine Branch II

### Vi Commands

j=down

k=up

h=left

l=right

i=insert mode

:q!=cancel and quit

ESC=leave mode

:wq=save and quit

### Recursive Merging

Git cannot fast forward since changes were made in both the masterand the adminbranch

## Branch Shortcut

$ git checkout -b admin

Creates and checks-out the branch with single command

# Collaboration Basics

## Send/Get Changes

Good practice to:

$ git pull

$ git push

This will help avoid getting rejected

1. $ git pullwill fetch (or sync) the local repo with the remote repo—same as a $ git fetch
  1. There are actually two branches—rigin/masteron the local repo and masteron the remote (GitHub) repo
2. The pull merges the rigin/masterwith master
  1. This is the same as running $ git merge origin/master

## Fix Conflicts

$ git commit -a

# Branching

## Push Branch

Create new branch (shopping\_cart) and switch to new shoppint\_cartbranch

Rhyddid:sandbox-git Jason$ git checkout -b shopping\_cart

Switched to a new branch &#39;shopping\_cart&#39;

Link local branch to remote branch (tracking)

Rhyddid:sandbox-git Jason$ git push origin shopping\_cart

Total 0 (delta 0), reused 0 (delta 0)

To https://github.com/BluePawDev/sandbox-git.git

 \* [new branch]      shopping\_cart -&gt; shopping\_cart

## Get Remote Branch

$ git branch -r

Lists all remote branches

## Remote Branches

$ git remote show origin

This will show all:

- remote branches and if they are tracked or not
- local branches and which remote branches they merge with
- local branches configured for when we do a $ git push
- local branches that are out of date

## Delete on Remote

$ git push origin :shopping\_cart

This only deletes the remote branch—the local branch will still exist

To delete local branch, the following will error

$ git branch –d shopping\_cart

This is gittrying to prevent deleting unmerged changes

To override, use capitol D

$ git branch –D shopping\_cart

## Branch Status

$ git remote show origin

## Clean Branches

$ git remote prune origin

This is something you want to run occasionally, especially on large projects

### Heroku

$ git push heroku-staging staging

Will not work, would push staging to staging because Heruko only deploys master branch

$ git push heroku-staging staging:master (local:remote)

This will push from local to master and deploy

## List Tags

Tags are basically a reference to a specific commit—used mostly for release versioning

To list all tags:

$ git tag

To review, check out code at commit:

$ git checkout v0.0.1

## Create Tags

To add a new tag:

$ git tag –a v0.0.3 –m &quot;version 0.0.3&quot;

## Send/Push Tags

To push new tags:

$ git push --tags

# Rebase belong to us

Merge commits are bad

## Rebase I

Instead of:

$ git pull

$ git push

Do this:

$ git fetch

$ git rebase

fetchpulls down any changes from GitHub, but **does not merge** them—syncs without merging

$ git rebasedoes three things:

1. Move all changes to masterwhich are not rigin/masterto a temporary area
2. Run all rigin/master commitsne at a time
3. Run all commitsin temporary area—on top of the master—one at a time

There are **no** merge commits

### Local Branch Rebase

$ git checkout admin

$ git rebase master

This will run master commits then run admin commits

$ git checkout master

$ git merge admin

Still may run into conflicts when using rebase

To work with possible conflicts:

$ git fetch

$ git rebase

This will:

1. Take all our commitsfrom masterand move them into a temporary area
2. Then run all the rigin/master commits
3. Then run all commitsin the temporary area one at a time

This will cause a conflict

The options are:

$ git rebase --continue

$ git rebase --skip

$ git rebase --abort

Running $ git statuswill show we&#39;re not on any branch because we&#39;re in the middle of the rebase

After editing the file:

$ git add README.txt

$ git rebase --continue

# History and Configuration

## Short History



## Show Changes



## Branch Changes



## Ancestor Commits

## History with Diff



## Whose Line Is It?



## Ignore Files



## Configuration



## Global Config



## Alias
