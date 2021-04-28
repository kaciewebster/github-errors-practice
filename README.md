# Git Practice

A helpful guide to some common problems I've seen using Git, along with some great resources!

![](https://imgs.xkcd.com/comics/git_2x.png)

## "Large files detected ... error: failed to push some refs to ..."

This error is caused by trying to push a file that is over 100 MB, which is the GitHub file limit. This problem can be solved many different ways depending on how you want to treat your large files. I like to remove them from my remote repository and keep them in my local repository.

Example: Try to add and push this [data](https://www.kaggle.com/yamaerenay/spotify-dataset-19212020-160k-tracks). It should fail.

**Solution**

**Use this solution if your file was pushed for the first time in your last commit:**

1. Add and open a .gitignore file within your repository

2. Add the names of the large files to your .gitignore file

3. Save and close the .gitignore file

4. In the terminal, run these commands

```python
# Remove the large file from your committed changes but not your computer.
git rm -rf --cached <large file name>

# Add changes.
git add .

# Amend the previous commit with your change.
git commit --amend -CHEAD

# Push your changes without the large file.
git push
```

[Solution Link](https://stackoverflow.com/questions/32953238/how-can-i-ignore-big-files-and-push-to-git-repo)

## "Your local changes to the following files would be overwritten by merge ..."

This error is usually caused when there were some changes to the remote repository that you are trying to pull but they interfere will changes you've made to your local repository.

Example: Pulling the DSI lectures.

**Solution**

1. In your terminal within the repository, run these commands

```python
# Save your local changes aside and revert your working repository back to the original.
git stash

# Pull the new changes to your working repository.
git pull

# Add the changes that you stashed back into your working repository.
git stash pop
```

Solution was posted in Slack by Ryan.

## You forked a repository and want to pull the changes from the original repository.

This isn't so much a problem but a situation that I've seen some students come across. When you fork a repository, you are taking a snapshot of the original and working off of that. A git pull won't be able to pull any changes that are made to the original repository.

Example: Forking the DSI lectures and then cloning it to your local machine.

**Solution**

1. In your terminal within the repository, run these commands

```python
# Adds an upstream path to the original repository that you forked from.
git remote add upstream <original repository url>

# Downloads changes, but doesn't add them to your local respository.
git fetch upstream

# Pulls those changes into your local repository.
git pull upstream master
```

[Solution Link](https://gist.github.com/CristinaSolana/1885435)

## Resources

[Git Handbook](https://guides.github.com/introduction/git-handbook/)

[Basic Git Commands](https://www.hostinger.com/tutorials/basic-git-commands)

[Solutions to Common Git Problems](https://medium.com/@bellex0/git-reference-guide-solutions-to-common-git-issues-cb375972a367)

[Common Git Problems and their Fixes](https://www.geeksforgeeks.org/common-git-problems-and-their-fixes/)