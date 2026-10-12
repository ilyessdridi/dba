        *******    Here is the complete PowerShell command we used to configure Oracle SQL*Plus permanently for horizontal output   ******
New-Item -ItemType Directory -Force C:\OracleConfig | Out-Null

@'
set linesize 300
set pagesize 1000
set wrap off
set colsep ' | '
column name format a35
column value format a60
column issys_modifiable format a20
'@ | Set-Content C:\OracleConfig\login.sql

[Environment]::SetEnvironmentVariable("SQLPATH", "C:\OracleConfig", "User")


      ******** shortcut in MobaXterm to open sql plus as SYS and HR  *********************
cat >> ~/.bashrc <<'EOF'

# Oracle SQL*Plus shortcuts
alias oracledba='/drives/c/oraclexe/app/oracle/product/11.2.0/server/bin/sqlplus.exe / as sysdba'
alias oraclehr='/drives/c/oraclexe/app/oracle/product/11.2.0/server/bin/sqlplus.exe hr'
EOF
source ~/.bashrc

 
