# Environment Configuration (WSL + Ubuntu + RubyMine) #

- Installing WSL
```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```
Restart your machine, then install Ubuntu from the Microsoft Store. Once installed, open Ubuntu (or invoke wsl in the command prompt) and create your user credentials.

---

- Installing Ruby on Rails
```
sudo apt-get update

sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev

cd
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec $SHELL

git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
exec $SHELL

rbenv install 3.0.0
rbenv global 3.0.0
ruby -v

gem install bundler

curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

sudo apt update
sudo apt-get install -y nodejs yarn
gem install rails -v 6.1.1
rbenv rehash
rails -v
```

---

- RubyMine Configuration

First navigate to ```Settings → Languages & Frameworks → Ruby SDK and Gems```. (or press ```Ctrl+Alt+S``` and type ```SDK``` in search bar)

![image](https://user-images.githubusercontent.com/28052029/111370014-74df8280-8676-11eb-82ff-a9014c0ce7d5.png)

![image](https://user-images.githubusercontent.com/28052029/111370668-47df9f80-8677-11eb-8586-71e0e7040414.png)

For Ruby or version manager path, enter the following, replacing <version> with your Ruby version and <username> with the username used for your Windows filesystem: ```/home/<username>/.rbenv/versions/3.0.0/bin/ruby```
  
Then go to Terminal configuration and replace the Shell path with the following: ```wsl.exe```

![image](https://user-images.githubusercontent.com/28052029/111371358-0bf90a00-8678-11eb-8681-d9babec85f7a.png)
