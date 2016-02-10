---
title: Git Cheatsheet
---

### TLDR
`pull or init > (add / rm / modify) > commit > push`

[Version Control for the Humanities with Git Workshop](https://github.com/xpmethod-workshops/githum)

### Starting a New Project
1. `git init` to start watching the current directory  
2. `git add foo.txt` to stage the file  
3. `git commit -m "my first commit notes"` describe your changes  
4. `git remote add origin https://github.com/denten/dhnotes` point to the
remote repo  
5. `git push -u origin master` push to remote for the first time  
  
### Syncing with an Existing Project
`git clone https://github.com/denten/dhnotes` clone the remote then rejoin the
above instructions at step 2.
 
`git pull` before doing anything
  
> note: `git pull` does a `git fetch` followed by a `git merge`  
  
`git add/rm foo.txt`  
Stage any new files you want to commit. Modified files will be staged
automatically. `git reset` to unstage. Add new files with add and remove with
rm. Use the --amend flag to amend the commit before pushing  

> use `git commit -am "notes go here"` to combine add and commit in one line
  
`git push` to push changes to the server  

### Fork and Pull Request Model of Contribution

1. Click to fork, by going to the team's project repository (R1). This creates
a copy or a "fork" of the repository in your own account (R2).

2. Clone your own repository (R2) down to your machine (L2).

3. Make some changes.

4. Push your changes from your local machine (L2) to your own remote
repository
(R2).

5. Navigate to your repository (R2) using your browser. Click to create a
"pull
request," which asks the moderators of the teams repository (R1) to accept
your
changes from R2.

You will have to go through this process for each change. If you contribute
frequently to the same team project you may want set up a
[sync](https://help.github.com/articles/syncing-a-fork/) between R1 and R2. In
the language of Git you will set R1 as "upstream" of R2.

### Diagnostics
`git diff` to see the diffs on your modified files  
  
`git status` is your best friend  
  
`git log --graph`  
  
`git remote -v` to show fetch and push locations  
  
`git remote show origin`  

### Branching
1. Make a new branch and switch to it: `git checkout -b edits`
2. Edit your files
3. Commit your changes to advance head: `git commit -am "notes"`
4. Switch back to master: `git checkout master`
5. Merge the patch: `git merge edits`

### Submodules
Submodules are repositories within repositories. Try to avoid this, but useful
for syncing your vim settings, for example, which will have other git repos
attached. Also useful to manage GitHub Wikis.  
  
`git clone --recursive git://github.com/foo/bar.git` to clone including the
submodules  
  
`git submodule add https://github.com/user/repo` to add submodules to an
existing project  
  
`git submodule init` if the files are not pulling
  
`git submodule update` to update your submodules  
  
`git submodule foreach git pull origin master` or `git pull
--recurse-submodules origin master` to upgrade all submodules

if the head gets detached run `git checkout master`  

`git submodule deinit` followed by `git rm name-of-submodule` to remove
submodule (Git 1.8.5+)  
  
if the submodule head gets detached, run `$ git checkout master` from the
submodule directory followed by `git pull`. See [this
tutorial](http://web.archive.org/web/20140203045532/http://www.vogella.com/tutorials/Git/article.html)
for more information. See the Github Tips section for Wiki handling.



### Tips

- Use SSH instead of HTTPS to avoid storing unencrypted credentials locally
(or logging in with every push / pull). Follow the instructions here to [set
up ssh](https://help.github.com/articles/generating-ssh-keys). SSH will allow
you to use your keyring on a Mac or do `ssh-add` on Debian linux once per
session.

- To clone a project without the top directory run `$ git clone PATH .` But
that will only work for an empty directory. If the directory is not empty
follow the `git init` route (as you would with a new repo and `remote add
origin` as usual.

- `git add -A` to add all untracked files and directories  

#### Create a new branch identical with the old one

```
git checkout -b new_branch old_branch
git push origin new_branch
```

- GitHub Pages
TBA

#### Wikis
- Add your wiki to the repo as a submodule by running `$ git submodule add -b
master [URL to Git repo].wiki.git`. The submodule allows you to edit the wiki
locally, in markdown. Use [gollum](https://github.com/gollum/gollum) to
preview locally, if needed.
- Note that the submodule points to a specific revision. Make changes and
commit / push in the submodule as usual. Run `$ git submodule update --remote`
in the parent directory to update the pointer to the correct revision.
- This will mean that for every change in the wiki you have to push twice,
once to the wiki (from the submodule directory) and once to the main
repository, from the root repo folder.
- The wiki tool on gitHub will always have the latest revision.
- If the head gets detached run `$ git checkout master` in the submodule
directory.

#### Merge Conflicts

- Install *p4merge* on Mac, *WinMerge* on Windows, or *Meld* on Linux.
- run `git config --global merge.tool p4merge` to set your default merge tool
- `git mergetool` after "unable to merge" errors


