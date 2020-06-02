# Git

## Remove file from entire git history
From https://help.github.com/articles/removing-sensitive-data-from-a-repository/
```bash
git filter-branch --force --index-filter \
'git rm --cached --ignore-unmatch PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA' \
--prune-empty --tag-name-filter cat -- --all
```

## Add to gitignore
```bash
echo "YOUR-FILE-WITH-SENSITIVE-DATA" >> .gitignore
git add .gitignore
git commit -m "Add YOUR-FILE-WITH-SENSITIVE-DATA to .gitignore"
```

## Copy full repo to another one (dont work on zsh)
```bash
git clone <from_repo_url>
git remote add newrepo <new_repo_url>
git push newrepo --tags 'refs/remotes/origin/*:refs/heads/*'
```
