# **eFlow 4.1 - GET/PUT very slow ** #

## **Question / Description** ##

A customer is experiencing a slow-down in the following workflow:


![](http://i.imgur.com/jVL1upm.jpg)

CPU usage is stable at 85-90% (no peaks up to 100%) while memory is used way below its limit, so the system is not particularly stressed.

As you can see from the picture the PreExport station is the critical bottleneck (MaxWorkUnit = 10). I roughly monitored the “real” processing time counting from when collections get locked in the controller until when they get released.

It takes just few seconds (10-20). But it takes more than 2 minutes until other 10 collections get locked.

The WF db relies on the same machine, so I tend to exclude network issues mining the GET/PUT operations. Even if with a minor impact, I experienced the same behavior also on the recognition stations (all having MaxWorkUnit = 1).
 
Restarting eFLOW and the server didn’t help. No errors in the logger.
 
What can be the cause of this slowness? Too many collections in the Workflow database? Anything else?


## **Answer / Solution** ##

1)Clean up your Invoice Reader statistics if they are enabled! Specially Table StatisticsField

2)Check your workdir on all processing machines(that run EDC /FreeMatch/Process PReExport). Clean up any unnecessary files that are in such directory. Ideally delete the client dir.

3)I strongly advise to change MaxWorkUnit = 10 to MaxWorkUnit = 1. Simple auto sometimes “does not like” to work with more than one collection at a time.

4)Change Standby, Timer and idle interval to 1. You will have a quite fast pre-export after that.


----------

In my view CPU at 85-90% is quite overloaded already.  Another thing is about using Max Work Unit.  The Get/Put for 10 Max Work Unit will be slow because it needs to put 10 and get 10 then lock etc.  Not advisable to do that.  Meanwhile Readahead is more useful as it is running concurrently.  If there is no such need then avoid all these.  As Fernando advised, have 1 Max Work Unit.
 
Another factor to check is how many collections are in the flow?

Max performance is 10k, 30k will start to go slow if you are using controller. No controller usage then you can go to several hundreds of thousands.
 
Next to check your eFLOW version – TISXML or DB Management?

If DB Management then what is the build version that you used (Most stable is 4.5.2.174 + 5-7 more patches)?
 
Check your eFLOW Daemon service and customisation, do you have a lot of calls from clients (auto and manual) to server?
 
Another important maintenance, if you had processed many collections then (if it is still happening / depend on version) then there could be a lot of empty folders left behind in eFLOW Dynamics folder.  Need to restart application to clear them.
 
Also check if Anti-virus is running on those folders, it can slow your process down and at times conflict on file access, giving you failure/issues.


----------

This is a very old application running on a 4.1, way before DBM (way before I was in TIS actually).
Statistics (both eFlow and IR) are disabled.

I applied your and Fernando’s suggestion and set the config of the stations with all the times and workunits set to 1. For the PreExport we have roughly 15 seconds between Put and get. Still too much I assume.

I think that the responsible is this guy here:

![](http://i.imgur.com/h4dhfzp.png)

Probably SQL Server Express cannot handle such load of collections, and the interactions with the WF db are extremely slow. 

I know that we strongly discourage Express editions, particularly in production, and I guess this is the main reason.
 
I will suggest them to remove the over 3000 collections from the Clean station and to process the other 3000 they have in Completion before injecting new invoices into the system.

And of course to upgrade their SQL server if they need to handle such loads.


----------

1.      MaxWorkUnit set back to 10 – in this case you have bottleneck on ERPExport station so it’s not the “SimpleAuto” case described by Fernando. And also the case described by Fernando has a place only when the customization has been done wrongly. This parameter is exactly to speed up the process and especially to reduce the number of calls to DB – so if there are no customization contraindications it will be much faster with 10 instead of 1.

2.      SQL Express is not recommended for production but it can still handle up to 10 000 000 records so this is also rather not your problem.

3.      The CPU utilization is quite high but I suspect there are some other stations working on the same machine – check what is using this CPU.

4.      The number of collections in the workflow is also not too high – just remember ItalianCensus and up to 250k collections in the workflow and the slowness came when we had around 50k in one queue.
 
What to check:

1.      Exclude eFlow and Output folders from Antivirus

2.      Exclude eFlow and Output folders from Indexing – this is slowing a lot

3.      Check which processes are using this CPU so much

4.      Check temp folders – maybe there is some garbage if yes then stop everything and clean it up

5.      Check output folder:

a.      How many files in the output folder – if more than 1k then this is your reason

b.      Where is the output folder? Local or network? If network then it can be your reason.

6.      Check DB server – is it only used for eFlow or for any other purposes?

7.      Try to understand what changed in the system from the moment it started to be slow - I guess before it was ok.
 
Let me know what have you found for “check” section then maybe I’ll be able to suggest you more.


----------

Thanks a lot for the very detailed walkthrough.

The problem was in the WorkDir, where more than 20000 files (TIF, REG, mostly PRD) accumulated. 

Cleaning this folder did the magic.





















