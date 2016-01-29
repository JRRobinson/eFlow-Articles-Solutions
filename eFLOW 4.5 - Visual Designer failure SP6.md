# **eFLOW 4.5 - Visual Designer failure SP6 ** #

## **Question / Description** ##

When I try to change any EFI Properties on visual designer from windows 2008 server @ customer UAT environment 

[__MSG_START__]00746
DATE=19/09/14 15:48:49.9228513;SEVERITY=ERROR;MODULE=DesignerMain;PID=efDesigner.exe:4048;USER=NYSDTF\T57920
MSG=Access violation at address 0BC15249 in module 'TISVIE~1.DLL'. Read of address 00000000
STACK_TRACE=   at System.Environment.GetStackTrace(Exception e, Boolean needFileInfo)
   at System.Environment.get_StackTrace()
   at TiS.TisCommon.Log.Write(Severity enSeverity, String sSource, String sDetails, String sFormat, Object[] Params)
   at TiS.TisCommon.Log.Write(Severity enSeverity, String sSource, String sFormat, Object[] Params)
   at TiS.Core.eFlowAPI.TisSimpleLogger.RequestMessageLog(String Message, String UnitName, TIS_SEVERITY Severity, Int32 SubCategories, Int16 Category)
[__MSG_END__]00746
[__MSG_START__]00743
DATE=19/09/14 15:48:57.4733481;SEVERITY=ERROR;MODULE=DesignerMain;PID=efDesigner.exe:4048;USER=NYSDTF\T57920
MSG=Access violation at address 40070AF3 in module 'Vcl50.bpl'. Read of address 0000014C
STACK_TRACE=   at System.Environment.GetStackTrace(Exception e, Boolean needFileInfo)
   at System.Environment.get_StackTrace()
   at TiS.TisCommon.Log.Write(Severity enSeverity, String sSource, String sDetails, String sFormat, Object[] Params)
   at TiS.TisCommon.Log.Write(Severity enSeverity, String sSource, String sFormat, Object[] Params)
   at TiS.Core.eFlowAPI.TisSimpleLogger.RequestMessageLog(String Message, String UnitName, TIS_SEVERITY Severity, Int32 SubCategories, Int16 Category)
[__MSG_END__]00743
[__MSG_START__]04397
DATE=19/09/14 15:49:11.1391233;SEVERITY=WARNING;MODULE=TiS.TisCommon;PID=eFlowDmn.exe:2868;USER=NYSDTF\PTTMSSVC
MSG=Perfom task on all nodes. Details : TiS.Core.PlatformRuntime.Management.Server.DomainChangeNotificationTask,    at System.Environment.GetStackTrace(Exception e, Boolean needFileInfo)
   at System.Environment.get_StackTrace()

![](http://i.imgur.com/hZ20qgZ.png)

![](http://i.imgur.com/SYkGO2M.jpg)



## **Answer / Solution** ##

Short answer: Run Tray as Administrator, open module activator from tray, open VD from module activator and there is no issue.

Long answer: Still unclear, the user used to run tray/VD is in the Admin group of the machine. Will reply again if I can find some answer in the security policies.































