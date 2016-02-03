# **eFlow 5 - old vs new - SQL connections different behaviours** #

## **Question / Description** ##

After upgrading from 5.0.2.2 to 5.1 SP1 my SimpleAuto station started to raise exceptions 
 
The timeout period elapsed prior to obtaining a connection from the pool.  This may have occurred because all pooled connections were in use and max pool size was reached.



## **Answer / Solution** ##

It turned out that there were SqlConnection, SqlTransaction, SqlReader involved in the database communication – every second a connection/transaction/reader was opened, but then only the reader and transaction would be rolled back.
There was no closing of SqlConnection though.
It never happened problems with 5.0.2.2 and the system runs 24/7 with this one.
 
I checked with this query
select * from sys.sysprocesses where hostprocess = <process id> order by login_time
 
and with the old eFlow there were max 66-68 connections, basically the old connections were being dropped pretty fast.

With the new eFlow I saw that the old connections were dropped too, but not that fast – the number of connection easily reached 100 within minutes – and then on an attempt to open a new connection, problems started to appear.
 
Basically closing the connection solved all the issues.
 
It’s just interesting that the behavior of old eFlow vs new eFlow is different – as if there was some feature within SimpleAuto that alters the default SQL settings.







