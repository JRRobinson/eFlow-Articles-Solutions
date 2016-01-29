# **eFlow 4.5 - Error locking collections in Completion ** #

## **Question / Description** ##

A customer is not managing to get any collection in a Completion station in a Client installation.
In the log appears next message (linked to eflowDmd.exe PID): 
 
Exception of type TiS.TisCommon.TisException [SQL Failed: [LockQueueTopUnits], Msg: Incorrect syntax near ')'.]
 
While if launched from another machine collections can be processed properly.
 
What could be causing this situation ?



## **Answer / Solution** ##

Cleaning AppData folder in the Client fixed the situation.


























