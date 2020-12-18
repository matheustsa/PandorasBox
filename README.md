# Utils #

#### GitHub Markdown ####
https://guides.github.com/features/mastering-markdown/

### GIT - Remove .idea from git project ###
```
echo '.idea' >> .gitignore
git rm -r --cached .idea
git add .gitignore
git commit -m 'remove .idea folder from project'
git push
```
