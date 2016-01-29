# **eFlow 4.5 - Daylight Saving Time ** #

## **Question / Description** ##

Are there any known issue with daylight saving time clock change?
 
On Sunday we had clock change, on Monday one customer had all modules inactive and in the error log 

“DbAutoTransaction.Dispose:Commit failed, performing RollbackTransaction”.   

The issue was resolved by restarting everything. Still the customer would like to know the cause. And if it was related to the clock change, what to do to avoid that when the next clock change comes in October?
 

## **Answer / Solution** ##

In 4.5 SP5, one of our customer have change the date by mistake (they said), when the first station started, it corrupted the license.

![](http://i.imgur.com/sCHqMZg.png)

I don´t know if a time zone change can corrupt the license somehow. I hope not. I don´t know if the behavior above is the same for eFLOW 5.
 
In 4.5, other problem we have seen with license is about the expiration. For instance, if the license expires today, while the server is not restarted (eFLOW service), the customer is being able to use the software until the next restart, even with the license expired. I hope this doesn´t happen in eFLOW 5.






















