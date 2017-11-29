# Quick Git Review

## Vocab
branch: A copy of the main repository as a basis for new changes.
HEAD: Currently checked out *commit*
commit: A revision. A set of file changes saved to the repository.
index/stage/cache: Staging area for changes that have not yet been committed. Cache.
push: send commits to a different repository (usually Github)
pull: retrieve commits from a different repository (usually Github)
remote: A different repository. Has a name and an address (http/ssh)

Common Commands:
```
git init
git clone http://github.com/repositoryname
git pull remote_name branch_name
git push remote_name branch_name [--force]
git checkout -b new_branch_name
git rebase branch_name_to_rebase_to
git reset [--soft --hard] branch_name_to_reset_to
git add -u [.]
git remote add remote_name remote_address
```

Git Workflow:

1. Create a fork from the main project repository (upstream).
2. Clone your newly forked repository to your machine (origin).
3. Pull down the latest changes from upstream.
4. Create a new branch to begin making your own changes.
5. Add and commit your changes.
6. Check if there are any new changes upstream by rebasing with upstream/master.
7. Push your branch to Github.
8. Create a pull request.

During the workflow you’ll do various other common things like delete files, add files, make multiple commits, add new remotes and experiment with new branches. This is safe and normal to do!

To avoid conflicts, try not to work on the same thing as your teammates. In those situations, pair programming is the answer.


## FAQ

__Why do I need this?__

Git is a file storage and versioning system. This allows you to save every version ever of anything you're
working on. 

__What can I do with git?__

You can experiment with code safely using git. Without git, every change you make has the potential to break your application. With git, you can use branches to test anything and everything then save only the changes you like.

__How can I create a new branch when I've already *staged* (git add) new changes?__

You can:
- Unstage files: `git rm directory/filename.ext`
- You can create a new branch before committing: 
`git checkout -b newbranch`

__...what if I *committed* the new file/folder?__

Then you can just create a new commit (recommended) or:
- Rollback the commit and then remove it: 
`git reset --soft commit_hash; git rm filename.ext --cached`
- Delete the file and amend the commit: 
`git commit --amend -m "Commit message."`


__What if the master branch has changed while I was making changes?__

- Commit your changes: `git add . && git commit -m "Commit message."`
- Rebase your branch: `git rebase master`

__Is my repository on Github?__

Only if you push it to Github. Think of Github as cloud storage for your repo. Your repository is local in a folder on your computer named `.git`. That's your repository. 

__What are remotes?__

They are links to other repositories. They allow you to share code.

__I have a ton of commits on this branch. Can I squash them into one?__

Yes:
```
# To edit the last 3 commits:
git rebase -i HEAD~3

# Now you'll be in interactive mode. You will see instructions on what you can do.
# This will squash the last 2 commits into the first:
pick 0EC247 Commit one.
s 0BA379 Commit 2.
s 0F7378 Commit 3.
```

__How do I resolve a merge conflict?__

Git will point out the conflicts to you and list the exact files where they occur. Open each file and sit down with the author with whom your changes conflict. Discuss the changes and determine which parts of the code will be committed.

Then push the changes.

Things you’ll hear and see by advanced git users:
- cherry-pick
- diff
- format-patch
- apply

More Reading:
https://help.github.com/articles/github-glossary/
http://blog.osteele.com/2008/05/my-git-workflow/
https://robots.thoughtbot.com/git-interactive-rebase-squash-amend-rewriting-history



