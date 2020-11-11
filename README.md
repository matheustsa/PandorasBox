# Utils #

## DOKKU - Useful commands ##
Miscellaneous useful commands
Run Rake tasks: ```dokku run myapp rake db:migrate```

Open Rails console: ```dokku run myapp rails c```

Tail Logs: ```dokku logs myapp -t```

NGINX logs
- access: ```dokku nginx:access-logs myapp```
- errors: ```dokku nginx:error-logs myapp```


Restart the app: ```dokku ps:restart myapp```

Check docker process: ```docker ps```

Remove unused Dokku: ```dokku cleanup```



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

### RAILS - Set user passwd via console ###
```bash
rails console -e production
```
```bash
user = User.where(id: 1).first
```
```bash
user.password = '123456'
```
```bash
user.password_confirmation = '123456'
```
```bash
user.save!
```
Extra: send email notification informing that admin changed your password
```bash
user.send_only_admin_changed_your_password_notification!
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
