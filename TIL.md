https://gist.github.com/leandromonaco

# GitHub

## Reset author for ALL commits
```
git filter-branch -f --env-filter "GIT_AUTHOR_NAME='Newname'; GIT_AUTHOR_EMAIL='new@email'; GIT_COMMITTER_NAME='Newname'; GIT_COMMITTER_EMAIL='new@email';" HEAD
git push --force --tags origin 'refs/heads/main'
```

## Read Git Configuration
```
git config -l
```

## Removing sensitive data from a repository
- https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository
- https://rtyley.github.io/bfg-repo-cleaner/

## Troubleshoot git issues

```
set GIT_TRACE=1
set GIT_CURL_VERBOSE=1
```

# NodeJS

## Installation with [Node Version Manager](https://github.com/coreybutler/nvm-windows)

```
nvm install latest
nvm install lts
nvm install 12.18.4
nvm list
nvm use 12.18.4
nvm current
```

# WinGet

Install [winget](https://winget.run) and search packages

```
winget install Microsoft.VisualStudioCode --override '/SILENT /mergetasks="!runcode,addcontextmenufiles,addcontextmenufolders"'
winget install -e --id Postman.Postman
```
