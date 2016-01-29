# **eFlow 4.5 - ePortal ERROR Import PDF ** #

## **Question / Description** ##

A customer is reporting that a few pdf documents are not being imported into the system. In the logger, the following type of error:
 
DATE=28/01/15 13:22:27.9767652;SEVERITY=ERROR;MODULE=ePortal: ePortal;PID=efSimpleAuto.exe:5688;USER=GROUP\sa.digitmail01it
MSG=Could not find file 'C:\IR-DATA\Runtime\ePortal\Default\EWS_Pirelli_0114\78c591f8-546f-42f9-b26c-ea7a53e29248\ATTACH\403d1b21-22fa-471b-9885-a64b4b663750\ORIG\1160336-415000118-20150106-CBS-CID-IT201-20150107013245.pdf'.

STACK_TRACE=   at System.Environment.GetStackTrace(Exception e, Boolean needFileInfo)
   at System.Environment.get_StackTrace()
   at TiS.TisCommon.Log.Write(Severity enSeverity, String sSource, String sDetails, String sFormat, Object[] Params)
   at TiS.TisCommon.Log.Write(Severity enSeverity, String sSource, String sFormat, Object[] Params)
   at TiS.Core.eFlowAPI.TisSimpleLogger.RequestMessageLog(String Message, String UnitName, TIS_SEVERITY Severity, Int32 SubCategories, Int16 Category)
   at TiS.Import.ePortal.ePortalStation.StationLogger.LogError(String message)
   at TiS.Import.ePortal.ePortalEngine.EPortalEngine.ProcessEBatch(IEPortalDatabase database, EBatch eBatch)
   at TiS.Import.ePortal.ePortalEngine.EPortalEngine.Process()
   at TiS.Import.ePortal.ePortalStation.ePortalStation.OnPostGetCollections(ITisClientServicesModule oCSM)
   at System.RuntimeMethodHandle._InvokeMethodFast(Object target, Object[] arguments, SignatureStruct& sig, MethodAttributes methodAttributes, RuntimeTypeHandle typeOwner)
   at System.RuntimeMethodHandle.InvokeMethodFast(Object target, Object[] arguments, Signature sig, MethodAttributes methodAttributes, RuntimeTypeHandle typeOwner)
   at System.Reflection.RuntimeMethodInfo.Invoke(Object obj, BindingFlags invokeAttr, Binder binder, Object[] parameters, CultureInfo culture, Boolean skipVisibilityChecks)
   at System.Reflection.RuntimeMethodInfo.Invoke(Object obj, BindingFlags invokeAttr, Binder binder, Object[] parameters, CultureInfo culture)
   at TiS.Core.PlatformRuntime.Customizations.ManagedMethodInvoker.InvokeMethod(String sAssemblyName, String sClassImplName, String sMethodName, Object[]& InParams)
   at TiS.Core.PlatformRuntime.Customizations.TisDNEventInvoker.Invoke(ITisInvokeParams oInvokeParams, ITisEventParams oEventParams, Object[]& InOutParams)
   at TiS.Core.PlatformRuntime.Customizations.TisEventsManager.FireEvent(Object oEventSource, ITisEventParams oEventParams, Object[]& InOutParams)
   at TiS.Core.PlatformRuntime.Customizations.TisEventsManager.FireEvent(Object oEventSource, Object oEventBindingKey, String sEventName, Object[]& InOutParams)
   at TiS.Core.PlatformRuntime.Customizations.TisServiceEventsAdapter.OnEventInterceptionHandler(ITisEventsManager oEventsManager, Object oEventSource, Object oEventBindingKey, String sEventName, Object[]& InOutParams)
   at TiS.Core.eFlowAPI.TisSimpleAutoStationDeclaration.OnPostGetCollections(ITisClientServicesModule )
   at TiS.Core.eFlowAPI.TisCollectionsGetStationDeclaration.FireEvent_OnPostGetCollections(ITisClientServicesModule oCSM)
   at TiS.Applications.SimpleAuto.AutoStationLogic.GetCollections()
   at TiS.Applications.SimpleAuto.AutoStationLogic.PerformStationLoop()
   at TiS.Applications.SimpleAuto.AutoStationLogic.StationMainThread()
   at System.Threading.ThreadHelper.ThreadStart_Context(Object state)
   at System.Threading.ExecutionContext.Run(ExecutionContext executionContext, ContextCallback callback, Object state)
   at System.Threading.ThreadHelper.ThreadStart()
[__MSG_END__]03449
 
 
Emails have then been archived under the ePortal ERROR folder.
 
Has anybody faced this issue with ePortal before or has some idea of what might have caused it?

## **Answer / Solution** ##

The problem was about the length of the filename. Shortening the attachment name the error does not occur anymore.

Although the length of path bold in the log below is under the file system limit (which should be 260 chars), I suppose that during the process, ePortal uses some temp folders/files whose path gets longer than 260.
 
Maybe something to fix for next version.

























