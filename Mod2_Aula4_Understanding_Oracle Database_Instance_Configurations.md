$ ls /usr/local/bin

$ . oraenv
? orcl

$ cat /etc/oratab

$ env | grep ORA

$ sqlplus / as sysdba

### Subindo o banco de dados

SQL> statup nomount;

SQL> shutdown immediate;

SQL> SELECT COUNT(*) FROM V$SESSION;

SQL> ALTER DATABASE MOUNT;

SQL> ALTER DATABASE OPEN;

### Derrrubanco o banco de dados

SQL> ALTER DATABASE CLOSE;

SQL> SELECT OPEN_MODE FROM V$DATABASE;

SQL> SELECT STATUS FROM V$INSTANCE;

SQL> ALTER DATABASE DISMOUNT;

SQL> SHUTDOWN;


### Iniciando o Banco
SQL> STARTUP;

### Checkpoint
SQL> ALTER SYSTEM CHECKPOINT;