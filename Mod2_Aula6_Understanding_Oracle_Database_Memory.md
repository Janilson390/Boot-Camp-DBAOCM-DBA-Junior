# Understanding Oracle Database Memory
---------------
## Comandos
### Entrando na instância
sqlplus / as sysdba

### Iniciando a instância
SQL> startup nomount; *Inicia a instância alocando a memoria e colocando os processos em background*

SQL> show parameter sga

SQL> set lines 200 pages 10000

SQL> select * from V$SGAINFO; *Informações da SGA*

SQL> select * from V$SGA_TARGET_ADVICE; *Informações da SGA*

SQL> select * from V$MEMORY_TARGET_ADVICE ORDER BY MEMORY_SIZE; *Informações da SGA*

SQL> alter database flashback on; *Habilita a flashback area do banco*

SQL> alter database flashback on; *Desabilita a flashback area do banco*

ps -ef | grep rvwr *mostra o processo do flashback rodando ou não*

cd /u02/fst_recovery_data/ORCL/flashback/ *Onde está os aquivos do flashback log*

SQL> select SUM(pga_max_men) AS pga_max_men, SUM(pga_max_men)/1024/1024 AS "TOTAL MAX PGA (MB)" from V$PROCESS; *Valor total da PGA*

SQL> set lines 200 pages 10000
col program format a65

select  spid, program,
        pga_max_mem     max,
        pga_alloc_mem   alloc,
        pga_used_mem     used,
        pga_freeable_mem     free
from    V$PROCESS; *Mais detalhes da PGA*

SQL> select estimated_flashback_size/1024/1024/1024 "EST_FLASHBACK_SIZE (GB)" from V$flashback_database_log; *Tamanho do flashback log do banco*