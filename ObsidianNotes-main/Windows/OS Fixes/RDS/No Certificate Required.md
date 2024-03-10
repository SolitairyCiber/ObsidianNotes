RDS without certificate check. on rds server powershell.  
Import-Module RemoteDesktop 
Set-RDSessionCollectionConfiguration –CollectionName QuickSessionCollection -CustomRdpProperty “authentication level:i:0”
 
