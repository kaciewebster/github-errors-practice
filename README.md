# Git Practice

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

## Third problem

## Resources

[Git Commands Cheat Sheet](https://www.hostinger.com/tutorials/basic-git-commands)

[Common Git Problems and Solutions](https://www.geeksforgeeks.org/common-git-problems-and-their-fixes/)