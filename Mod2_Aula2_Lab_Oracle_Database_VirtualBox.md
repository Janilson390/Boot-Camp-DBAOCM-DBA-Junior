# Laboratório Oracle Database 19c em uma Máquina Virtual

### Softwares

Oracle Linux 7.7
Oracle Database 19c
Virtual Box

### Tutorial

Após instação da máquina virtual, fazer esses procedimentos

- # ip addr *para vê o ip atual da máquina*
- # ping www.google.com.br *testanto a conectividade com a internet*
- # yum install oracle-database-preinstall-19c *pacote de pre-instalação com os pre-requisitos para isntalação do oracle database*
- # vi /etc/sysconfig/network-scripts/ifcfg-enp0s3 *modificar o arquico de configuração da interface de rede para o ip ser dinâmico*
> BOOTPROTO="static"
> IPADDR=192.168.0.112

- # reboot

- # up addr

- # vi /etc/hosts
> 192.168.0.112 ol7-dba.localdomain  ol7-dba

- # ping ol7-dba

- # ping ol7-dba.localdomain

- # passwd oracle *Definindo uma senha para o usuário oracle*

- # vi /etc/selinux/config
> SELINUX=disabled

- # systemctl stop firewalld
- # systemctl disable firewalld

- # mkdir -p /u01/app/oracle/product/19.0.0/dbhome_1 *instalação do oracle software*
- # mkdir -p /u02/oradata *criação do banco da dados*

- # chown -R oracle:oinstall /u01 /u02 *Atribuindo o status de "dono" aos usuários oracle e oinstall dessas pastas*

- # chmod -R 775 /u01 /u02 *permissões para os diretórios*

- $ cd /u01/app/oracle/product/19.0.0/dbhome_1 
- $ unzip -op /home/oracle/{arquivo do oracle} *descompactar o arquivo de instalaçãop do oracle*
> diretório base é o */u01/app/oracle*. Dentro dele, posso ter outros homes.
- $ ls -ltrh *checando os arquivos do diretório*
- $ du -h *checar a quantidade de arquivos de dentro de um diretório*

- $ ./ruminstaller

# Testando a instalaçãp
- $ .oraenv
> orcl

- $ cat /etc/oratab

- $ ps -ef|grep smon

- $ lsnrctl status

- $ sqlplus / as sysdba

- SQL>  show pdbs *vê os pluggables database*

- SQL> exit

