# RUBY AND RAILS #

### Env install and config (ruby 3.0.0 and rails 6.1.1 with rvm using postgres) ###

- #### System ####
```
sudo apt-get update
sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev libgdbm-dev libncurses5-dev automake libtool bison
```

- #### RVM ####
```
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
curl -sSL https://get.rvm.io | bash -s stable
source ~/.rvm/scripts/rvm
rvm install 3.0.0
rvm use 3.0.0 --default
ruby -v
```

- #### Rails ####
```
gem install rails -v 6.1.1
```

- #### Node and Yarn ####
```
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

sudo apt update
sudo apt-get install -y redis-server redis-tools nodejs yarn
```

- #### Git ####
```
git config --global color.ui true
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR@EMAIL.com"
ssh-keygen -t rsa -b 4096 -C "YOUR@EMAIL.com"

cat ~/.ssh/id_rsa.pub

https://github.com/settings/keys

ssh -T git@github.com
```

- #### Postgres ####
```
sudo apt-get install -y postgresql libpq-dev
sudo su postgres
createuser --interactive
ubuntu
y 
exit
```

- #### New Project ####
```
rails new myapp -d postgresql
cd myapp
bundle
rails db:create db:migrate
rails s
```

### RAILS - Routes ###
http://localhost:3000/rails/info/routes

### RubyMine plugins ###
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
##### If you need to connect to console in dokku, see DOKKU.md (https://github.com/matheustsa/PandorasBox/blob/main/DOKKU.md) #####

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
