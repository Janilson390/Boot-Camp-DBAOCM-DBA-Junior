### Inicializando as variáveis de ambiente

~~~console
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

~~~console
# mkdir -p /backup/rman
# chown oracle:oinstall -R /backup/
# chmod 775 -R /backup/
~~~

Fazendo o bakup (arquivo biário)
~~~sql
SQL> ALTER DATABASE BACKUP CONTROLFILE TO '/backup/rman/control.bkp' 
~~~

Fazendo backup (arquivo texto)
~~~sql
SQL> ALTER DATABASE BACKUP CONTROLFILE TO TRACE; 
~~~

### Listando os Data Files
~~~sql
SQL> SELECT MEMBER FROM V$LOGFILE;
SQL> SELECT NAME FROM V$DATAFILE;
SQL> SELECT VALUE FROM V$PARAMETER WHERE NAME =
'control_files'; 
~~~

### Criando um novo Control File
~~~sql
CREATE CONTROLFILE
 SET DATABASE prod
 LOGFILE GROUP 1 ('/u01/oracle/prod/redo01_01.log','/u01/oracle/prod/redo01_02.log'),
 GROUP 2 ('/u01/oracle/prod/redo02_01.log','/u01/oracle/prod/redo02_02.log'),
 GROUP 3 ('/u01/oracle/prod/redo03_01.log', '/u01/oracle/prod/redo03_02.log')
 RESETLOGS
 DATAFILE   '/u01/oracle/prod/system01.dbf' SIZE 3M, 
            '/u01/oracle/prod/rbs01.dbs' SIZE 5M, 
            '/u01/oracle/prod/users01.dbs' SIZE 5M, 
            '/u01/oracle/prod/temp01.dbs' SIZE 5M
 MAXLOGFILES 50
 MAXLOGMEMBERS 3
 MAXLOGHISTORY 400
 MAXDATAFILES 200
 MAXINSTANCES 6
 ARCHIVELOG;
~~~

### Backup Aotomatico via RMAN

Entrando no RMAN
~~~console
$ rman target /
~~~

Listando todos os parametros
~~~console
RMAN> show all;
~~~

~~~console
RMAN> CONFIGURE CONTROLFILEAUTOBACKUP ON;
RMAN> CONFIGURE CONTROLFILE AUTOBACKUP FORMAT FOR DEVICE TYPE DISK TO '/backup/rman/cf_%F';
~~~

### Backup Manual via RMAN
Entrando no RMAN
~~~console
$ rman target /
~~~

Backup manual
~~~console
RMAN> COPY CURRENT CONTROLFILE TO '/backup/rman/control.bkp';
~~~








