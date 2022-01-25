
# GitHub

## Reset author for ALL commits
```
git filter-branch -f --env-filter "GIT_AUTHOR_NAME='Newname'; GIT_AUTHOR_EMAIL='new@email'; GIT_COMMITTER_NAME='Newname'; GIT_COMMITTER_EMAIL='new@email';" HEAD
git push --force --tags origin 'refs/heads/main'
```
