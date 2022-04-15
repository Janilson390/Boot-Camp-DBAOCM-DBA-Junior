# ESTRUTURAS DE PROCESSOS DO ORACLE

## PROCESSOS MANDATÓRIOS
-----------
### PMON - PROCESS MONITOR PROCESS
### PMAN - PROCESS MANAGER PROCESS
### LREG - Listener Registration Process
### SMON - System Monitor Process
### DBWn - Database Writer Process
- n indica a quantidade de DBW da sua instância.
### CKPT - Checkpoint Process
### MMON - Manageability Monitor Process
### MMNL - Manageability Monitor Lite Process
### RECO - Recoverer Process
### LGWR - Log Writer Process

## PROCESSOS ADICIONAIS
---------
### ARCn - Archivver Process
- n indica a quantidade de processos que fazem o arquivamento na sua instância.
### CJQ0 - Job Queue Coordinator Process
### RVWR - Recovery Writer Process
### FBDA - Flashback Data Archive Process
### SMCO - Space Management Coordinator Process

## PROCESSOS SLAVES (BACKGROUND)
---------
### Dnnn - Dispatcher Process
### Snnn - Shared Server Process

- show parameter DISPATCHERS
- show parameter SHARED_SERVERS
- show parameter MAX_SHARED_SERVERS
- show parameter LOCAL_LISTENER
- show parameter REMOTE_LISTENER


