### Inicializando as variáveis de ambiente
~~~
oracle$ . oraenv
 orcl

oracle$ sqlplus / as sysdbs
~~~

### Consultando Control File do Oracle
~~~sql
SQL> show parameter control_file;
~~~

~~~sql
SQL> show parameter db_create;
~~~

### Backup do Control File do Oracle

Criando o diretório onde vai ficar o backup
~~~
# mkdir -p /backup/rman
# chown oracle:oinstall -R /backup/
# chmod 775 -R /backup/
~~~

Fazendo o bakup
~~~
SQL> ALTER DATABASE BACKUP CONTROLFILE TO '/backup/rman/control.bkp' 
~~~

