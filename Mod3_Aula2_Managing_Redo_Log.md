### View V$LOG

~~~sql
SQL> SELECT GROUP#, THREAD# FROM V$LOG;

SQL> COL CURRENT_SCN FOR  99999999999999999999;
SQL> SELECT CURRENT_SCN FROM V$DATABASE;
~~~

### Status do Redo Log

~~~sql
set term on
set linesize 210
set feed off
col file_name for a15 wrap
col first_time for a19
col first_change# for 99999999999999999999
col tam for 9999999.99
col mbytes for 9999999.99
select  group#,thread#,sequence#,bytes/1024/1024 mbytes,
        members,archived,status,first_change#,
        to_char(first_time,'dd/mm/yyyy hh24:mi:ss') first_time
  from  v$log;

  select    substr(lf.member,instr(lf.member,'\',-1)+
            instr(lf.member,'/',-1)+
            instr(lf.member,']',-1)+1) file_name,
            l.bytes/1024/1024 tam,
            l.thread#, l.status,first_change#,
            to_char(first_time,'dd/mm/yyyy hh24:mi:ss') first_time
  from      v$logfile lf,v$log l
 where      lf.group# = l.group#
order by    lf.member;
~~~

Mudando o redo log 

~~~slq
SQL> alter system switch logfile;
~~~

### Archive Mode

~~~sql
SQL> archive log list;
~~~

### Limpando um Redo Log File

~~~sql
SQL> ALTER DATABASE CLEAR LOGFILE GROUP 1;
~~~

~~~sql
SQL> ALTER DATABASE CLEAR UNARCHIVED LOGFILE GROUP 1;
~~~