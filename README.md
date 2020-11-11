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

##### UBUNTU - Disable network printers auto install #####
```bash
sudo systemctl stop cups-browsed
sudo systemctl disable cups-browsed
```

### POSTGRES ###
```
CREATE TABLE new_table AS 
TABLE table_to_import 
WITH NO DATA;
```

```
select * from A 
  where (col1, col2) not in
   ( select col1, col2 from B )
```
