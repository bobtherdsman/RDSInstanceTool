# RDSInstanceTool
SQl server To RDS Instance matching tool :
Installation Steps: 
****should be  installed  on a computer with Excel sheet ****
1-Extract RDSSqlServerInstanceTool.zip on c:\RDSSQL 
  The tool has 2 files RdsInstanceTool.exe and RDSSQLInstances.  
2- Create an input file that contain a list of all your Sql Server that you are trying to match with RDS 
  Instance and place it in c:\RDSSQL 
  You can use IP address or SQL Server name and if port is different than the default port, enter the port as well as shown below. 
3- Installation complete 
 Running RDSInstanceTool 
  To execute open a CMD prompt navigate to c:\RDSSQL and type: 
  C:\RDSSQL>RDSqlServerInstanceTool.exe login password file type  
  Login: Sql server login 
  Password: Sql server login password  
  File: the input file created in step 2 
  Type: M- for memory optimized instances G- for general purpose instances 
Output: 
The output will look like the screen shot below; a great effort is made to match your on prem resources with the right RDS instance. Few things are considered while matching your resources with an RDS instance: 
  1-Not all instances are available for all Sql server version and edition. 
    A complete list of instances per Edition and version can be found in this link 
    https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_SQLServer.html#SQLServer.Concepts.General.InstanceClasses 
  2-I try to match your CPU first with the RDS instance and this mean that it is possible that the instances that I am suggesting could be overprovisioned on RAM. 
    For example, in below screen shot server #2 has 36 CPU and 60 GB RAM allocated, the    
    closet that I can match with 10xlarge for general purpose which is 40 CPU and 160 GB RAM. Downsizing to 8xlarge will end up well below the 36 CPU. So, review all       
    suggestion and refer to below link to adjust to the right instance that woks for you at the end of the day you would  
    know your need and your server requirements. 
    https://aws.amazon.com/rds/sqlserver/instance-types/ 
  3-the tool as of today will only match standard and Enterprise Edition with Minimum of 4 CPU (Xlarge)  
  4- 10xlrage is only available for general purpose instances not for Memory Optimized. 

 

 

 

 
