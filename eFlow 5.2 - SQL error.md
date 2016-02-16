# **eFlow 5.2 - SQL error** #

## **Question / Description** ##

We’re currently at a customer’s, trying to install eFlow 5.2. We’re hitting the issue wherein the eFlow DBs (Mgt and Monitor) are not getting created. Tried multiple iisresets. AppPool user (domain acct) is sysadmin, can create DB on server.

The error logged in SQL log is:

“Login failed for user ‘ABC’. Failed to open the explicitly specified database.”



## **Answer / Solution** ##

Additional info regarding the error. There were DirectoryNotFoundException errors in TIS_Logs complaining about eFlow not being able to access H:\SQL_Logs folder (this is the Log folder on the remote SQL server). We confirmed that the domain account (that’s running TisAppPool) can see and access (read/write) this folder. 

Don’t know why eFlow doesn’t see it.

We tried to create the eFlow_Management and eFlow_Monitor DB shells to see if eFlow would be able to populate the DBs with objects. Didn’t help (which is consistent with error above).

We then ran scripts to populate the eFlow_Management and eFlow_Monitor DBs and it worked after that.

So we investigated further and found the issue (which I vaguely remembered seeing with earlier versions of eFlow as well).

Here’s the analysis in case you’re interested.

Our customer’s environment setup

eFlow on server A. Server A has 2 physical drives: C & D. eFlow is installed on drive D.
	
-	SQL is remote, on server B. Server B has 4 physical drives, C, D, H & I. In SQL, mdf files are configured to be on D:\SQL_Data\ while ldf files are configured to be on H:\SQL_Logs\.

What we confirmed happened (at least in eFlow 5.2):

-	When eFlow is installed (or iisreset), eFlow tries to create the eFlow_Management & eFlow_Monitor DBs (expected). However, we found that it first somehow tries to create a SQL_Data folder on D:\ and SQL_Logs folder on H:\ of the eFLOW server.
	
-	It’d be able to create the SQL_Data folder on D:\ but was not able to create the SQL_Logs folder on H:\ because the eFlow server does not contain an H:\ drive (we’d get an error in TIS_log saying it can’t find the H:\SQL_Logs\ directory). This caused the eFlow_Management and eFlow_Monitor DBs to not get created.

-	Once we switched the Log path on SQL from H:\SQL_Logs to D:\SQL_Logs (or C:\SQL_Logs), it worked fine, i.e. DBs got created automatically by iisreset. If we run manually the scripts to create those DBs, it’d work too.


