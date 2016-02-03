# **eFlow 5 - Station login failed** #

## **Question / Description** ##

Due to a power outage, a server went off.

The inappropriate closure damaged eFLOW 5 in a way that is no longer usable (every login in a station, fails).

Error message is something like the one below (details in the attachment) :

FATAL Source App: efControl.exe, Message: 
TISAppenderLog4net.LogConfiguration+Log4NetException: Application login into [OGK5] as station [efControl] failed, Station login failed. ---> System.Runtime.InteropServices.COMException: Application login into [OGK5] as station [efControl] failed, Station login failed.


What I tried :

-	iisreset ;

-	TisAppPool restared few times ;

-	Tis Web Site restarted ;

-	eFLOW 5 restarted ;

-	Server restarted (again).

Still crashing every time on every login.
Any other steps I can try ?




## **Answer / Solution** ##

Fixed.

Credits to Ben.

I was not so diligent in checking all the lines in the Event Viewer as him

There was below a visible “License failure”.


The crash impacted the Admin module as it was wrongly requiring the activation again.













