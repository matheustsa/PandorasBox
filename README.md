# Utils #

#### GitHub Markdown ####
https://guides.github.com/features/mastering-markdown/

### Remove .idea from git project ###
```
echo '.idea' >> .gitignore
git rm -r --cached .idea
git add .gitignore
git commit -m 'remove .idea folder from project'
git push
```

#### RubyMine plugins ####
https://plugins.jetbrains.com/plugin/12778-quick-file-preview


##### Disable network printers auto install #####
```bash
sudo systemctl stop cups-browsed
sudo systemctl disable cups-browsed
```

### Reset ID sequence in database ###
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
