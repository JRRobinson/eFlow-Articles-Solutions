# **eFlow 4.5 SP6: Can't see the list of autorun** #

## **Question / Description** ##

When I click on the Autorun Stations in Enterprise Manager, instead of showing the list of the configured autorun stations, I get the following error:

![](http://i.imgur.com/6CgUH6k.png)

BaseErrorHandler.WriteShowError: Error : System.NullReferenceException: Object reference not set to an instance of an object.
   at TiS.Applications.EnterpriseManager.Details.TisAppStationsView.GetMaxNumberOfInstances(ITisPreconfiguredStation oStation)
   at TiS.Applications.EnterpriseManager.Details.TisAppStationsView.PrepareViewData()

Any suggestion would be appreciated.



## **Answer / Solution** ##

Issue solved: a station (FilePortal) that does not exist anymore in the WF was still defined in the list of Autorun stations because I updated the CAB without previously removing it from the autorun stations.

I managed to remove it with eflowcmd:
eflowcmd AutorunEntryRemove <ApplicationName> <NodeName> <StationName>

And now I can show the list of the autoruns in the Enterprise Manager.
