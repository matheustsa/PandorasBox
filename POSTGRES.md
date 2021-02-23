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
