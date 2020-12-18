## DOKKU - Useful commands ##

#### Process and Container Management ####
http://dokku.viewdocs.io/dokku~v0.7.0/deployment/process-management/#process-and-container-management

#### SSL Configuration ####
http://dokku.viewdocs.io/dokku~v0.20.4/configuration/ssl/

#### Nginx ####
http://dokku.viewdocs.io/dokku~v0.4.1/nginx/

#### Miscellaneous ####
Run Rake tasks: ```dokku run myapp rake db:migrate```

Open Rails console: ```dokku run myapp rails c```

Tail Logs: ```dokku logs myapp -t```

##### NGINX logs #####
- access: ```dokku nginx:access-logs myapp```
- errors: ```dokku nginx:error-logs myapp```


Restart the app: ```dokku ps:restart myapp```

Check docker process: ```docker ps```

Remove unused Dokku: ```dokku cleanup```


### Connection and Database ###
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