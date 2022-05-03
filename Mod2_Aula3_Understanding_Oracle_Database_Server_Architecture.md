### Arquivos do Database

cd /u02/oradata/ORCL19C/datafile

ls -ltrh *Lista dos arquivos de dados do banco de dados ORCL19C*

### Derrubando uma instância

sqlplus / as sysdba

SQL> shutdown immediate;

SQL> ! ps -ef | grep smon *Com ! você pode rodar comandos linux no SQLPlus*

### Stattando a instância mas não o banco

sqlplus / as sysdba

SQL> statup nomount;

SQL> ! ps -ef | grep smon *Com ! você pode rodar comandos linux no SQLPlus*

### Arquivo de trace no controfile

sqlplus / as sysdba

SQL> alter database backup controlfile to trace; *Gera um arquivo de trace do controlfile do banco*

SQL> exit;

cd /u01;app/oracle/diag/rdbms/orcl19c/orcl19c/trace

ls -ltrh

view {ultimo arquivo.trc}

### Abrindo os pluggable databases do CDB

sqlplus / as sysdba

SQL> show con_name; *onde você está conectato*

SQL> alter pluggable database all open;

SQL> show pdbs;

### Navegando entre os PDBs ou CDB

SQL> alter session set containner=pbd1; *Vai para o PBD1*

SQL> alter session set containner=cdb$root; *Vai para o cdb$root;*

### Outros arquivos do Oracle

cd $ORACLE_HOMR/dts

ls -ltrh

### Criando um arquivo pfile (parameter file)

sqlplus / as sysdba

SQL> create pfile='/home/oracle/initorcl19c.ora' from spfile;

SQL> exit;

view /home/oracle/initorcl19c.ora *Esse arquivo inicializa a instancia*

### Visualizando os parametros

sqlplus / as sysdba

SQL> show parameter process; 

OU 

SQL> sho parameter process;

SQL> sho parameter db_rec

SQL> alter system set db_recovery_file_dest_size=6G scope=both; *parametro dinâmico*

SQL> alter system set db_recovery_file_dest_size=6G scope=spfile; *parametro estaticos. Reinicia a instâcia pra mudar*






