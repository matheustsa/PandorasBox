## DOKKU - Useful commands ##

#### Miscellaneous useful commands ####
Run Rake tasks: ```dokku run myapp rake db:migrate```

Open Rails console: ```dokku run myapp rails c```

Tail Logs: ```dokku logs myapp -t```

##### NGINX logs #####
- access: ```dokku nginx:access-logs myapp```
- errors: ```dokku nginx:error-logs myapp```


Restart the app: ```dokku ps:restart myapp```

Check docker process: ```docker ps```

Remove unused Dokku: ```dokku cleanup```


### Cnnection and Database ###
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
\x
TABLE mytablename;
\COPY my_table TO '/tmp/my_table.csv' CSV HEADER DELIMITER ';'
scp my_table.csv mtsa@__IP__:~/Downloads/
```
