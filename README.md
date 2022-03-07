# RDSInstanceTool
Sql server To RDS Instance matching tool:
Installation Steps: 

**** should be installed on a computer with Excel sheet and powershell ( with Sqlserver Module installed)  
   More about the sql server module https://docs.microsoft.com/en-us/sql/powershell/sql-server-powershell?view=sql-server-ver15
   Your Maleware may flag this as a risk since it is an exe but it is totaly safe to run, this is just simpley a compiled Powershell script 
****

1-Extract RDSSqlServerInstanceTool.zip on c:\RDSSQL
  The tool has 2 files RdsInstanceTool.exe and RDSSQLInstances.xlsx.
  
2- Create an input file that contains a list of all your Sql Server that you are trying to match with RDS Instance and place it in c:\RDSSQL 
 Sample file is attached.

  You can use IP address or SQL Server name and if port is different than the default port, enter the port as well as shown below. 
  sample file attached.
 
3- Installation complete 

 Running RDSInstanceTool:
 
  To execute open a CMD prompt navigate to c:\RDSSQL and type: 

 C:\RDSSQL> RDSInstanceTool.exe login password file type
 **i.e c:\rdssql\Rdsinstancetool.exe  sa passowrd1234 c:\rdsql\server.txt M**

  Login: Sql server login ( sa password or login  with access to dmv ) 
  
  Password: Sql server login password
  
  File: the input file created in step 2 
  
  Type: M- for memory optimized instances G- for general purpose instances 
  
Output: 
 A great effort is made to match your on prem resources with the right RDS instance,Few things are considered while matching your resources with an RDS instance: 
   
  1-Not all instances are available for all Sql server version and edition. 
    A complete list of instances per Edition and version can be found in this link 
    https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_SQLServer.html#SQLServer.Concepts.General.InstanceClasses 
    
  2-I try to match your CPU first with the RDS instance and this mean that it is possible that the instances that I am suggesting could be overprovisioned on RAM. 
    For example, a server with  36 CPU and 60 GB RAM allocated, the closet that I can match with 10xlarge for general purpose which is 40 CPU and 160 GB RAM.
     Downsizing to 8xlarge will end up well below the 36 CPU.
    So carefully Review all suggestion and refer to below link to adjust to the right instance that woks for you at the end of the day you would  
    know your need and your server requirements. 
        https://aws.amazon.com/rds/sqlserver/instance-types/ 
        
  3-the tool as of today will only match standard and Enterprise Edition with Minimum of 4 CPU (Xlarge)  
  4-10xlrage is only available for general purpose instances not for Memory Optimized. 
  
  Bugs:
   1-If Sqlserver Module is not loaded the app will fail
   2- Excel Sheet Com object reamins opened .
 
   
  
