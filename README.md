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

#### RubyMine plugins ####
https://plugins.jetbrains.com/plugin/12778-quick-file-preview


##### UBUNTU - Disable network printers auto install #####
```bash
sudo systemctl stop cups-browsed
sudo systemctl disable cups-browsed
```

### RAILS - Reset ID sequence in database ###
```bash
rails g task database reset_id_columns
```
```ruby
namespace :database do
    desc "Reset the sequence of auto-generated IDs to the last value already in table"
    task reset_id_columns: :environment do
        ActiveRecord::Base.connection.tables.each do |t|
            ActiveRecord::Base.connection.reset_pk_sequence!(t)
        end
    end
end
```
```bash
rake database:reset_id_columns
```

#### RAILS - Routes ####
http://localhost:3000/rails/info/routes


## Dokku ##
```
ssh 
dokku apps:list
dokku proxy:ports dare-hom
dokku logs dare-hom
dokku ps:restart dare-hom


dokku postgres:list
dokku postgres:info dare-homologacao-db
dokku postgres:expose dare-homologacao-db
dokku postgres:connect dare-homologacao-db


\dt 
TABLE mytablename;
\COPY my_table TO '/tmp/my_table.csv' CSV HEADER
scp my_table.csv mtsa@[-IP-]:~/Downloads/
```
