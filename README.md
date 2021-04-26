# Common GitHub Errors

![](https://imgs.xkcd.com/comics/git_2x.png)

## "Large files detected ... error: failed to push some refs to ..."

This error is caused by trying to push a file that is over 100 MB, which is the GitHub file limit.

Try to add and push this [data](https://www.kaggle.com/yamaerenay/spotify-dataset-19212020-160k-tracks)

**Solutions**

**Use this solution if your file was pushed for the first time in your last commit:**

1. Add and open a .gitignore file within your repository

2. Add the names of the large files to your .gitignore file

3. Save and close the .gitignore file

4. In the terminal, run these commands
```python
# Remove the large file from your repository, but not your computer.
git rm -rf --cached <large file name>

# Add changes.
git add .

# Amend the previous commit with your change.
git commit --amend -CHEAD

# Push your changes without the large file.
git push
```

