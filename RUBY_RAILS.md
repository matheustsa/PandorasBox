# RUBY AND RAILS INSTALL #

Follow instructions for [Ubuntu](https://gorails.com/setup/ubuntu/22.04) or [Windows](https://gorails.com/setup/windows/10)

Then:
  
```ruby
rails new myapp -n MyApp -d postgresql
```
Optional tags: `--css tailwind --skip-javascript`
```ruby
cd myapp/
bundle add rspec-rails bullet brakeman pry pry-byebug --group "development, test"
bundle add kaminari rubocop friendly_id formtastic devise turbo-rails stimulus-rails erb-formatter
rails generate tailwindcss:install
rails generate devise:install
rails turbo:install
rails turbo:install:redis
rails stimulus:install
rails g controller home index
rails g devise user
rails db:create db:migrate
rails s
```

#### Fix possible postgres error *"could not change directory to '/home/user': Permission denied"*

```stat -c "%G" <the problem folder, e.g. `/home/user`>```  
then  
```sudo usermod -aG <the output from last command> postgres```  

-----------

- #### ZSH + RBENV ####
```
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.zshenv
echo 'eval "$(rbenv init -)"' >> ~/.zshenv
echo 'source $HOME/.zshenv' >> ~/.zshrc
exec $SHELL
```

------------


- #### Oracle CLI ####
https://stackoverflow.com/questions/20084783/how-to-install-ruby-oci8-the-ruby-client-for-oracle-on-debian-based-systems-al

------------

### RAILS - Routes ###
http://localhost:3000/rails/info/routes

------------

### RubyMine plugins ###
https://plugins.jetbrains.com/plugin/12778-quick-file-preview

------------

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

------------

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

## Fix Gemfile.lock permission error ##
go to app folder, open terminal there and type:
```sudo chown -R $(whoami):$(whoami) $(pwd)```

------------

### Encode string in UTF-8 ###
```string.encode("UTF-8", :invalid => :replace, :undef => :replace, :replace => "?")```

### Working with directories ###
```https://www.rubyguides.com/2020/02/ruby-dir/```

------------

### Oracle OCI8 
```sudo apt-get install libaio-dev```

Download last ```BASIC``` and ```SDK``` .zip packages in: http://www.oracle.com/technetwork/database/features/instant-client/index-097480.html

```
echo "export LD_LIBRARY_PATH=/opt/oracle/instantclient_21_1" >> ~/.bashrc
exec bash
gem install ruby-oci8
```

------------
### Set NSL_LANG env var

```echo "export NLS_LANG=en_US.UTF-8" >> ~/.bashrc```
or
```echo "export NLS_LANG=$LANG" >> ~/.bashrc```

And don't forget to ```exec bash``` to reload your terminal

------------
### Redo migrations
https://riptutorial.com/ruby-on-rails/example/7069/redo-migrations

