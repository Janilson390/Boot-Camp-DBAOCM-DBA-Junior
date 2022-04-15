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
