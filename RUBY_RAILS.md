# RUBY AND RAILS #

#### RAILS - Routes ####
http://localhost:3000/rails/info/routes

#### RubyMine plugins ####
https://plugins.jetbrains.com/plugin/12778-quick-file-preview

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

### Set user passwd via console ###
```bash
rails console -e production
user = User.where(id: 1).first
user.password = '12345678'
user.password_confirmation = '12345678'
user.save!
```
##### If you need to connect to console in dokku, see DOKKU.md #####

- ##### Extra: send email notification informing that admin changed your password #####
```bash
user.send_only_admin_changed_your_password_notification!
```

### Fix Gemfile.lock permission error ###
go to app folder, open terminal there and type:
```sudo chown -R $(whoami):$(whoami) $(pwd)```

### Encode string in UTF-8 ###
```string.encode("UTF-8", :invalid => :replace, :undef => :replace, :replace => "?")```

### Working with directories ###
```https://www.rubyguides.com/2020/02/ruby-dir/```
