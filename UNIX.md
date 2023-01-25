# UNIX #
## Remap keyboard key ##
 1. First use the command ```xev``` in your terminal to find the KEYCODES for the keys you want to remap.
 
 2. Then use ```xmodmap -e "keycode [key to remap] = [new key]"```
 
 For example, if you want to remap PAUSE key to act like END key when pressed.
 
 ```xmodmap -e "keycode [PAUSE keycode] = [END keycode]"```
 
 Or just use its symbol ```xmodmap -e "keycode [PAUSE keycode] = End"```
 
 Alternatively ```setxkbmap``` command works too: ```setxkbmap -option "keycode 127=End"```.
 
 **PS: This will NOT persist after reboot.** To persist, you can create a script that contains the command, and then configure your system to run that script automatically on startup.

-----

## SSH Auth ##
```
https://linuxize.com/post/how-to-setup-passwordless-ssh-login/
```

## Mount directory with rw permissions ##
```
https://linuxize.com/post/how-to-mount-cifs-windows-share-on-linux/
```

------------

### Disable network printers auto install ###
```
sudo systemctl stop cups-browsed
sudo systemctl disable cups-browsed
```

### Convert file from iso-8859-1 to utf-8 using iconv ###
```iconv -f ISO-8859-1 -t UTF8//TRANSLIT SOURCE_FILE -o NEW_FILE```

### Start Service ###
```
sudo systemctl enable postgresql
```

systemctl:

- ```start``` - Start a service

- ```stop``` - Stop a service

- ```status``` - Show the status of a service

- ```enable``` - This enables a service so that it starts automatically

- ```disable``` - Don't start it automatically


### make install mkdir error
https://stackoverflow.com/questions/62160017/error-installing-rails-error-failed-to-build-gem-native-extension-ubuntu-20-0

----------------

## Set primary sound source on startup
Show sources with: ```pactl list short sinks```

Test switch: ```pactl set-default-sink <Your_Device_Name>```

Then add the same line to "Startup Applications" command text field

## Fix dual boot wrong time clock
```timedatectl set-local-rtc 1```
