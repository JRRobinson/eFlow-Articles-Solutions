# **eFlow 5.1 SP1 - Stations crashing in newly installed Environment (SimpleDemo)** #

### **Question/Description:** ###

On a new PROD environment, we are getting intermittent crashes with modules like FilePortal, Recognition of SimpleDemo.

Behaviour:
-	FilePortal would crash intermittently on Send All. Sample error:
2015-12-17 20:51:25,091 [1] FATAL Source App: Input.exe, Message: LockUnits : Session [18488] does not belong to queue [123].Process [Input] will be terminated.

2015-12-17 20:51:25,044 [5] FATAL Source App: /LM/W3SVC/2/ROOT/eFlow_5-3-130948867214036377, Message: 
TISAppenderLog4net.Log4NetException: Error in the application. ---> TiS.Core.TisCommon.TisWFIllegalSession: Error in the application.
   at TiS.Core.Application.Workflow.Model.Entities.CheckIllegalSession(Int32 sessionID, Int32 queueID, Boolean createCollection)
   at TiS.Core.Application.Workflow.Model.Entities.CreateUnit(String unitType, Int32 groupId, Int32 dataVersion, Int32 lastFinalQueue, Guid unitId, Double priorityLevel, Double prioritySubLevel, Double priorityLevelBoost, Double prioritySubLevelBoost, String flowType, String formType, String batchName, String name, String nextStation, Int32 numberOfForms, Int32 numberOfPages, Boolean anyBadPagesOrForms, Boolean requiresLearning, DateTime creationTime, Boolean createLocked, Int32 sessionID, DataTable tvpMetaTags, Int32 queueID, String nodeName, Nullable`1 slaID)
   at TiS.Core.Application.Workflow.Sql.WorkflowBaseSql.CreateUnit(Int32 sessionId, WFUnitInfo unitInfo, Boolean createLocked, WFCounter[] counters, IEnumerable`1& queues, String nodeName)
   at TiS.Core.Application.Workflow.WorkflowOperationsService.CreateUnit(Int32 sessionId, IEnumerable`1 targetQueues, WFUnitInfo unitInfo, Boolean createLocked, WFCounter[] counters, String nodeName)
   at TiS.Core.Application.Dynamic.DynamicService.CreateCollection(Int32 sessionId, Int32 queueId, CollectionData collectionData)
   at TiS.Core.Application.Dynamic.DynamicService.CreateCollections(Int32 sessionId, Int32 queueId, IEnumerable`1 collections)
   at TiS.Core.Application.Dynamic.DynamicService.ReleaseCollection(Int32 sessionId, Int32 queueId, KeyValuePair`2 collectionsReleaseInfo)
   at TiS.Core.Application.Dynamic.DynamicService.ReleaseCollections(Int32 sessionId, Int32 queueId, IEnumerable`1 collectionsReleaseInfo)
   at SyncInvokeReleaseCollections(Object , Object[] , Object[] )
   at System.ServiceModel.Dispatcher.SyncMethodInvoker.Invoke(Object instance, Object[] inputs, Object[]& outputs)
   at TiS.Core.TisCommon.Security.TisPermissionOperationInvoker.Invoke(Object instance, Object[] inputs, Object[]& outputs)
   --- End of inner exception stack trace ---
-	Recognition would crash intermittently during committing 
-	Recognition would encounter error when getting license, sample error:
2015-12-17 20:26:33,450 [52] FATAL Source App: /LM/W3SVC/2/ROOT/eFlow_5-1-130948725736635158, Message: 
TISAppenderLog4net.Log4NetException: License feature usage increase failed because node does not exist (most likely was disposed). Node name is 'efl-pro-rec01_efProcessShell_3240_15542271955944181379_1' ---> System.ServiceModel.FaultException`1[TiS.Core.Domain.License.Exception.LicenseFeatureNodeDoesNotExistException]: License feature usage increase failed because node does not exist (most likely was disposed). Node name is 'efl-pro-rec01_efProcessShell_3240_15542271955944181379_1'
   at TiS.Core.Domain.License.Storage.LicenseFeatureUsageStorage.UpdateUsage(String featureName, Int32 changeUsageCount)
   at TiS.Core.Domain.License.LicenseService.UpdateUsage(String featureName, Int32 changeUsageCount)
   at TiS.Core.Domain.License.LicenseService.IncreaseSessionUsage(String featureItemName, Int32 increaseUsageCount, String sessionId)
   at SyncInvokeIncreaseSessionUsage(Object , Object[] , Object[] )
   at System.ServiceModel.Dispatcher.SyncMethodInvoker.Invoke(Object instance, Object[] inputs, Object[]& outputs)
   at TiS.Core.TisCommon.Security.TisPermissionOperationInvoker.Invoke(Object instance, Object[] inputs, Object[]& outputs)
   --- End of inner exception stack trace ---


We checked the DB and found that the records are somehow deleted from E_Node table (eFlow_Management) shortly after station launch. Delete query seems to be triggered by IIS.


### **Answer/Solution:** ###

The issue is due to the eFlow server and SQL server are set to different time zones

