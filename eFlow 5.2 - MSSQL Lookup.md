# **eFlow 5.2 - MSSQL Lookup** #

### **Question/Description:** ###

I´m having an error message during completion where I set an mssql lookup
This is the connection string server=shamsqlimpc2.mpc-group.com; Integrated Security=True;database=eFlow_RefDB_MPC And the error message that the user don’t have right to read the table:


![](http://i.imgur.com/T2cI23r.jpg)

2015-12-16 13:44:53,822 [27] FATAL Source App: /LM/W3SVC/2/ROOT/eFlow_5-1-130946669456117067, Message: Der Benutzer hat nicht die Berechtigung, um diese Aktion auszuführen.
TISAppenderLog4net.Log4NetException: Der Benutzer hat nicht die Berechtigung, um diese Aktion auszuführen. ---> System.Data.SqlClient.SqlException: Der Benutzer hat nicht die Berechtigung, um diese Aktion auszuführen.
   at System.Data.SqlClient.SqlConnection.OnError(SqlException exception, Boolean breakConnection, Action`1 wrapCloseInAction)
   at System.Data.SqlClient.TdsParser.ThrowExceptionAndWarning(TdsParserStateObject stateObj, Boolean callerHasConnectionLock, Boolean asyncClose)
   at System.Data.SqlClient.TdsParser.TryRun(RunBehavior runBehavior, SqlCommand cmdHandler, SqlDataReader dataStream, BulkCopySimpleResultSet bulkCopyHandler, TdsParserStateObject stateObj, Boolean& dataReady)
   at System.Data.SqlClient.SqlDataReader.TryConsumeMetaData()
   at System.Data.SqlClient.SqlDataReader.get_MetaData()
   at System.Data.SqlClient.SqlCommand.FinishExecuteReader(SqlDataReader ds, RunBehavior runBehavior, String resetOptionsString)
   at System.Data.SqlClient.SqlCommand.RunExecuteReaderTds(CommandBehavior cmdBehavior, RunBehavior runBehavior, Boolean returnStream, Boolean async, Int32 timeout, Task& task, Boolean asyncWrite, SqlDataReader ds)
   at System.Data.SqlClient.SqlCommand.RunExecuteReader(CommandBehavior cmdBehavior, RunBehavior runBehavior, Boolean returnStream, String method, TaskCompletionSource`1 completion, Int32 timeout, Task& task, Boolean asyncWrite)
   at System.Data.SqlClient.SqlCommand.RunExecuteReader(CommandBehavior cmdBehavior, RunBehavior runBehavior, Boolean returnStream, String method)
   at System.Data.SqlClient.SqlCommand.ExecuteScalar()
   at Microsoft.Practices.EnterpriseLibrary.Data.Database.DoExecuteScalar(DbCommand command)
   at Microsoft.Practices.EnterpriseLibrary.Data.Database.ExecuteScalar(DbCommand command)
   at Microsoft.Practices.EnterpriseLibrary.Data.Database.ExecuteScalar(CommandType commandType, String commandText)
   at TiS.Core.Application.DbAccess.Provider.SQL.TisSqlDatabase.GetLastUpdateTime()
   at SyncInvokeGetLastUpdateTime(Object , Object[] , Object[] )
   at System.ServiceModel.Dispatcher.SyncMethodInvoker.Invoke(Object instance, Object[] inputs, Object[]& outputs)
   at TiS.Core.TisCommon.Security.TisPermissionOperationInvoker.Invoke(Object instance, Object[] inputs, Object[]& outputs)
   --- End of inner exception stack trace ---

### **Answer/Solution:** ###

There are two ways to solve the problem:

1.	Add the user to MSSQL-Database
2.	Don’t use „Integrated Security=true“, 
Use an DB-User with the expected rights and add the credentials to your 
Connection string.

