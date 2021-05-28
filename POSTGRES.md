# POSTGRES #

### Version ###
```
pg_config --version
```

------------

### Copiar tabela ###
```
CREATE TABLE new_table AS 
TABLE table_to_import 
WITH NO DATA;
```

------------

### Seleciona tudo da tabela A, que não estiver na tabela B ###
```
select * from A 
  where (col1, col2) not in
   ( select col1, col2 from B )
```

### remote connect ###
```
psql -h 127.0.0.1 -p 5432 -U postgres
```

https://avroblog.com/en/blog/content/How-to-restart-PostgreSQL

set local to <trust>
```
sudo gedit /etc/postgresql/12/main/pg_hba.conf
```

------------

  ### Import pg_dump from Heroku to localhost
  ```
  pg_restore --verbose --clean --no-acl --no-owner -h localhost -U <pg_user> -d <database> <heroku-dump>
  ```
