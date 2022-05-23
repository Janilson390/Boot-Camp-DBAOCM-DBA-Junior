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

SQL> ALTER SYSTEM SWITCH LOGFILE; //Troca o log file

SQL> ALTER SYSTEM CHECKPOINT;

SQL> CREATE TABLE ABC AS SELECT * FROM DBA_OBJECTS;

SQL> INSERT INTO ABC SELECT * FROM DBA_OBJECTS;

SQL> ALTER SYSTEM CHECKPOINT;

SQL> INSERT INTO ABC SELECT * FROM DBA_OBJECTS;

SQL> COMMIT;

SQL>SHUTDOWN ABORT;

SQL>STARTUP MOUNT;

SQL> ALTER DATABASE OPEN;

SQL>SHUTDOWN IMMEDIATE;

> SHUTDOWN: Derruba o banco, mas espera as ransações onsluirem e as sessões serem encerradas;
> SHUTDOWN ABORT: Derruba o banco imediatamente. Como se matasse o SMOM;
> SHUTDOWN IMMEDIATE: Derruba o banco imediatamente não aceitando novas conexões com o banco.

$ tail -1000f arquivo_log_oracle.log

SQL> STARTUP;

SQL> SELECT * FROM V$MEMORY_RESIZE_OPS; //Verifica o "Resize" dos processos do banco;

SQL> SELECT * FROM V$MEMORY_DYNAMIC_COMPONENTS;

Alocação e memoria
SQL> SELECT NVL(a.username, '(oracle)') AS Username,
            a.module,
            a.program,
            Trunc(b.value/1024) AS memory_kb
      FROM  V$SESSION a,
            V$SESSTAT b,
            V$STATNAME c
     WHERE  a.sid = b.sid
       AND  b.statistic# = c.statistic#
       AND  c.name = 'session pga memory'
       AND  a.program IS NOT NULL
  ORDER BY  b.value DESC;

SQLS QUE ESTÃO RODANDO NO BANCO
SQL> SELECT s.SID,
            s.STATUS,
            s.PROCESS,
            s.SCHEMANAME,
            s.OSUSER
            a.SQL_TEXT,
            p.PROGRAM
       FROM V$SESSION s,
            V$SQLAREA a
            V$PROCESS p
      WHERE s.SQL_HASH_VALUE = a.HASH_VALUE
        AND s.SQL_ADDRESS = a.ADDRESS
        AND s.PADDR = p.ADDR

Quanto que está sendo usado de PGS por sessão e qual serviço.
SQL> SELECT NVL(a.username, '(oracle)') AS Username,
            s.osuser,
            s.sid,
            s.serial#,
            p.spid,
            ROUND(p.pga_user_mem/1024/1024, 2) as pga_used_mem_md,    
            ROUND(p.pga_alloc_mem/1024/1024, 2) as pga_alloc_mem_md,
            ROUND(p.pga_freeable_mem/1024/1024, 2) as pga_freeable_mem_md,
            ROUND(p.pga_max_mem/1024/1024, 2) as pga_max_mem_md,
            s.lockwait,
            s.status,
            s.service_name,
            s.module,
            s.machine,
            s.program,
            TO_CHAR(s.logon_time, 'DD-MM_YYYY HH24:MI:SS') AS logon_time,
            s.last_call_et AS last_call_et_secs
       FROM V$SESSION s
            V$PROCESS p
      WHERE s.paddr = p.addr
   ORDER BY s.username, s.osuser;


SQL> SELECT NAME, VALUE FROM V$DIAG_INFO;

