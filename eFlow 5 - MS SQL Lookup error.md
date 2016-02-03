# **eFlow 5 - MS SQL Lookup error** #

## **Question / Description** ##

I´m having some trouble with an ms sql lookup under eflow 5 windows authentication,

Here is the error message

2015-11-04 14:58:26,239 [1] ERROR Source App: DataEntry.exe, Message: The query SELECT [Abteilung] FROM IRSuppliersAbteilung failed. Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: Invalid value for key 'integrated security'. (Fault Detail is equal to An ExceptionDetail, likely created by IncludeExceptionDetailInFaults=true, whose value is:
System.ArgumentException: Invalid value for key 'integrated security'.
   at System.Data.Common.DbConnectionOptions.ConvertValueToIntegratedSecurityInternal(String stringValue)
   at System.Data.SqlClient.SqlConnectionString..ctor(String connectionString)
   at System.Data.SqlClient.SqlConnectionFactory.CreateConnectionOptions(String connectionString, DbConnectionOptions previous)
   at System.Data.ProviderBase.DbConnectionFactory.GetConnectionPoolGroup(DbConnectionPoolKey key, DbConnectionPoolGroupOptions poolOptions, DbConnectionOptions& userConnectionOptions)
   at System.Data.SqlClient.SqlConnection.ConnectionString_Set(DbConnectionPoolKey key)
   at System.Data.SqlClient.SqlConnection.set_ConnectionString(String value)
   at Microsoft.Practices.EnterpriseLibrary.Data.Database.CreateConnection()
   at Microsoft.Practices.EnterpriseLibrary.Data.Database.OpenConnection()
   at TiS.Core.Application.DbAccess....).

the MS SQL definitions

server=srv17715.emmi.ch;trusted_connection=true;database=IREmmiTest_RefDB

any hints would be appreciate.


## **Answer / Solution** ##

Problem was with the config „Integrated security = true” and trusted_connection=yes






