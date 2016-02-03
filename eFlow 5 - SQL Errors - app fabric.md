# **eFlow 5 - SQL Errors - app fabric** #

## **Question / Description** ##

I see the errors in the log of the customer’s production;
It may be related to AppFabric;

The SQL Server is on the remote cluster and uses Windows authentication only.

Only one AppFabric service uses Network Service account – the 2 others run under Local Service.

The eFlow machine account is added to SQL security so AppFabric Caching Service can connect to the database.
But both Event and Workflow AppFabric services run under Local Service account – so obviously they can’t connect to the SQL (if they have to)

![](http://i.imgur.com/dQNEFfa.png)

Is my diagnosis correct ?

What is the impact ? eFlow seems to work.

What is the best way to fix this – change the user running both AppFabric Event and Workflow services from Local Service to Network Service?

Details below

Log Name - Microsoft-Windows-Application Server-System Services/Admin
Source - Application Server-System Services Workflow Management Service
USER: LOCAL SERVICE

Failed to obtain command from instance store 'defaultSqlPersistenceStore' (Root).\rException: Microsoft.ApplicationServer.StoreManagement.Sql.Control.SqlInstanceControlException: There was an error sending the control request. See the inner exception for details.
Inner Exception:
System.Data.SqlClient.SqlException: Login failed for user 'NT AUTHORITY\ANONYMOUS LOGON'..

Log Name - Microsoft-Windows-Application Server-System Services/Admin
Source - Application Server-System Services Event Collector
USER: LOCAL SERVICE

Unable to open database connection for the following application(s) (TIS Web Site/, TIS Web Site/TisDefaultSts, TIS Web Site/eFlow_5). Received exception. Message: Login failed for user 'NT AUTHORITY\ANONYMOUS LOGON'.. This event has occurred 44 times.


<Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event"> 
<System> 
<Provider Name="Microsoft-Windows-Application Server-Workflow Management Service" Guid="{C821412B-1624-4ABE-A845-50B2C98C2405}" /> 
<EventID>50939</EventID> 
<Version>0</Version> 
<Level>2</Level> 
<Task>0</Task> 
<Opcode>0</Opcode> 
<Keywords>0x8000000000000000</Keywords> 
<TimeCreated SystemTime="2015-03-02T14:31:56.622144100Z" /> 
<EventRecordID>1418535</EventRecordID> 
<Correlation /> 
<Execution ProcessID="1308" ThreadID="1460" /> 
<Channel>Microsoft-Windows-Application Server-System Services/Admin</Channel> 
<Computer>JWPPAVEFLOW01.ec.checkfree.com</Computer> 
<Security UserID="S-1-5-19" /> 
</System> 
<EventData> 
<Data Name="Name">defaultSqlPersistenceStore</Data> 
<Data Name="Location">Root</Data> 
<Data Name="ExceptionMessage">Microsoft.ApplicationServer.StoreManagement.Sql.Control.SqlInstanceControlException: There was an error sending the control request. See the inner exception for details. Inner Exception: System.Data.SqlClient.SqlException: Login failed for user 'NT AUTHORITY\ANONYMOUS LOGON'.</Data> 
<Data Name="OccurrenceMap">4</Data> 
<Data Name="Occurrences">25</Data> 
<Data Name="InstanceName">Nameless_WMS_Instance</Data> 
</EventData> 
</Event>

<Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event"> 
<System> 
<Provider Name="Microsoft-Windows-Application Server-System Services Event Collector" Guid="{A174E94E-A6F8-4041-9206-BF7B345729B0}" /> 
<EventID>126</EventID> 
<Version>0</Version> 
<Level>2</Level> 
<Task>0</Task> 
<Opcode>0</Opcode> 
<Keywords>0x8000000000000000</Keywords> 
<TimeCreated SystemTime="2015-03-02T14:32:18.275638100Z" /> 
<EventRecordID>1418536</EventRecordID> 
<Correlation /> 
<Execution ProcessID="1240" ThreadID="1860" /> 
<Channel>Microsoft-Windows-Application Server-System Services/Admin</Channel> 
<Computer>JWPPAVEFLOW01.ec.checkfree.com</Computer> 
<Security UserID="S-1-5-19" /> 
</System> 
<EventData> 
<Data Name="HostReference">TIS Web Site/, TIS Web Site/TisDefaultSts, TIS Web Site/eFlow_5</Data> 
<Data Name="ExceptionMessage">Login failed for user 'NT AUTHORITY\ANONYMOUS LOGON'.</Data> 
<Data Name="ExceptionData">
System.Data.SqlClient.SqlException (0x80131904): Login failed for user 'NT AUTHORITY\ANONYMOUS LOGON'.
at System.Data.SqlClient.SqlInternalConnection.OnError(SqlException exception, Boolean breakConnection, Action`1 wrapCloseInAction)
at System.Data.SqlClient.TdsParser.ThrowExceptionAndWarning(TdsParserStateObject stateObj, Boolean callerHasConnectionLock, Boolean asyncClose)
at System.Data.SqlClient.TdsParser.TryRun(RunBehavior runBehavior, SqlCommand cmdHandler, SqlDataReader dataStream, BulkCopySimpleResultSet bulkCopyHandler, TdsParserStateObject stateObj, Boolean& dataReady)
at System.Data.SqlClient.TdsParser.Run(RunBehavior runBehavior, SqlCommand cmdHandler, SqlDataReader dataStream, BulkCopySimpleResultSet bulkCopyHandler, TdsParserStateObject stateObj)
at System.Data.SqlClient.SqlInternalConnectionTds.CompleteLogin(Boolean enlistOK)
at System.Data.SqlClient.SqlInternalConnectionTds.AttemptOneLogin(ServerInfo serverInfo, String newPassword, SecureString newSecurePassword, Boolean ignoreSniOpenTimeout, TimeoutTimer timeout, Boolean withFailover)
at System.Data.SqlClient.SqlInternalConnectionTds.LoginNoFailover(ServerInfo serverInfo, String newPassword, SecureString newSecurePassword, Boolean redirectedUserInstance, SqlConnectionString connectionOptions, SqlCredential credential, TimeoutTimer timeout)
at System.Data.SqlClient.SqlInternalConnectionTds.OpenLoginEnlist(TimeoutTimer timeout, SqlConnectionString connectionOptions, SqlCredential credential, String newPassword, SecureString newSecurePassword, Boolean redirectedUserInstance)
at System.Data.SqlClient.SqlInternalConnectionTds..ctor(DbConnectionPoolIdentity identity, SqlConnectionString connectionOptions, SqlCredential credential, Object providerInfo, String newPassword, SecureString newSecurePassword, Boolean redirectedUserInstance, SqlConnectionString userConnectionOptions)
at System.Data.SqlClient.SqlConnectionFactory.CreateConnection(DbConnectionOptions options, DbConnectionPoolKey poolKey, Object poolGroupProviderInfo, DbConnectionPool pool, DbConnection owningConnection, DbConnectionOptions userOptions)
at System.Data.ProviderBase.DbConnectionFactory.CreatePooledConnection(DbConnectionPool pool, DbConnectionOptions options, DbConnectionPoolKey poolKey, DbConnectionOptions userOptions)
at System.Data.ProviderBase.DbConnectionPool.CreateObject(DbConnectionOptions userOptions)
at System.Data.ProviderBase.DbConnectionPool.UserCreateRequest(DbConnectionOptions userOptions)
at System.Data.ProviderBase.DbConnectionPool.TryGetConnection(DbConnection owningObject, UInt32 waitForMultipleObjectsTimeout, Boolean allowCreate, Boolean onlyOneCheckConnection, DbConnectionOptions userOptions, DbConnectionInternal& connection)
at System.Data.ProviderBase.DbConnectionPool.TryGetConnection(DbConnection owningObject, TaskCompletionSource`1 retry, DbConnectionOptions userOptions, DbConnectionInternal& connection)
at System.Data.ProviderBase.DbConnectionFactory.TryGetConnection(DbConnection owningConnection, TaskCompletionSource`1 retry, DbConnectionOptions userOptions, DbConnectionInternal& connection)
at System.Data.ProviderBase.DbConnectionClosed.TryOpenConnection(DbConnection outerConnection, DbConnectionFactory connectionFactory, TaskCompletionSource`1 retry, DbConnectionOptions userOptions)
at System.Data.SqlClient.SqlConnection.TryOpen(TaskCompletionSource`1 retry)
at System.Data.SqlClient.SqlConnection.Open()
at Microsoft.ApplicationServer.Monitoring.EventCollector.DatabaseWriter.SqlInitialize() ClientConnectionId:d09c1e07-b5a2-48c6-b1a9-c15ed27e2bd8</Data> <Data Name="OccurrenceMap">0</Data> 
<Data Name="Occurrences">1
</Data> 
<Data Name="InstanceName" /> 
</EventData> 
</Event>



## **Answer / Solution** ##

A customer encountered this before. I did some quick analysis and provided them with this info:

“AppFabric requires Service Principal Name (SPN)to be setup for the SQL server on the AD environment. For some reason, NTLM was not being used as an authentication mechanism. Adding an SPN entry for the SQL server should remove those error messages. 

Reference: [http://social.technet.microsoft.com/wiki/contents/articles/1566.windows-server-appfabric-troubleshooting-anonymous-logon.aspx](http://social.technet.microsoft.com/wiki/contents/articles/1566.windows-server-appfabric-troubleshooting-anonymous-logon.aspx)

They communicated this with their network team and they told me it’s fixed.













