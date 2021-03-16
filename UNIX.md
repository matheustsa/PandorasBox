# UNIX #
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
