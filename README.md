Git and GitHub

- Git is a VCS(Version Control System) or a SCM(Source Code Manager)
- version controlling, to collaborate, non linear development

Stages of Git
- Workspace : Where you are currently working in your local directory. This is the stage where git has not started tracking the files yet. Untracked files
- Staging area: Where the files become "tracked". You commit your files from here to store the files in the local repo
- Local Repo: This is the local repository on your laptop. You can get back versions and all here 
- Remote Repo 


git log : shows you all the commits you have made 

HEAD -> points to the most recent commit on your existing branch

sha id : the unique id for a commit. Using this sha id you can go back and forth in versions or even branch

git log --oneline : gives the sha id and the commit message only. Tbh this is the most useful command because its easy to read

git log --stat : gives you the whole history, including the file changes made basically all the details

git show sha_id : will show how the code was looking like at that version.

git diff : shows the changes made in the staging area
a/filename is the after and b/filename is the before

git checkout sha_id : takes you to that particular version.
git checkout master: takes you back to your original master branch. In my case I hadn't branched so master took me back to whatever latest version i was working with.

git branch branch_name sha_id : creates a branch from that particular commit

git branch : shows the branch, the asterisk shows which branch you're on

git log --oneline --all --graph : this shows the whole structure of the commits in the branch and the master in a graphical manner. Very useful 

git branch -d branch_name : deletes the branch, but make sure your current HEAD is not on the branch you're deleting. So you'll have to come to the master branch to delete the branch. A thing to notice is this returns an error if this branch is not merged with the master

git branch -D branch_name : deletes it anyway. Then again keep in mind that you'll have to be in the main branch to be able to do this operation.