# **eFlow 5.0.2.2 Weird issue with Completion (CAB created from empty CAB)** #

## **Question / Description** ##

A customer was developing a CAB using 5.0.2.2. They created a CAB using the empty CAB about a month ago. Things were working fine up until yesterday. Then out of a sudden, Completion stopped launching. The only error message is:

![](http://i.imgur.com/QzsmdBM.png)

Upon clicking on Save as File, this is displayed:

![](http://i.imgur.com/CARQ9ne.png)

No logs anywhere in Event Viewer, not in TIS_Log, not in Application, not in Security, not in Setup.
 
We tried to add completely new and blank Completion station (no custom events), removed all layouts. Still didn’t help. We made sure there’s no collection in the Completion queue. Didn’t help.
 
Other stations in the CAB are launching fine, i.e. Organizer, Collect, etc. Control is launching fine.
 
Other Completion stations in other CABs (including SimpleDemo) are working fine.
 
Is this because the CAB was created by the customer from the Empty CAB? Is there anything else I should check?


## **Answer / Solution** ##

Found that the CAB contains an MSSQL lookup table with incorrect lookup item settings (2 lookup items pointing to the same DB column). This cause Completion to crash.