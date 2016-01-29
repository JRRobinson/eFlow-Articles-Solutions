# **eFlow 5 - Recognition AccessViolationIssue** #

## **Question / Description** ##

I am encountering this error when running Recognition (IR CAB) in client’s environment:

Application: efProcessShell.exe
Framework Version: v4.0.30319
Description: The process was terminated due to an unhandled exception.
Exception Info: System.AccessViolationException
Stack:
   at TiS.Recognition.FreedomEngine.FreeformDllWrapper.FFRecognize(System.String, Int32, Int32 ByRef, System.Text.StringBuilder, Int32, Int32, Int32)
   at TiS.Recognition.FreedomEngine.FreedomAlg.Run(TiS.Recognition.FreedomEngine.IFECandidates, TiS.Recognition.FreedomEngine.FeBitmap, TiS.Recognition.Common.TPage)
   at TiS.Recognition.FreedomEngine.FreedomEng.RunFreedomAlg(TiS.Recognition.FreedomEngine.FFS, TiS.Recognition.FreedomEngine.FreedomConfiguration, TiS.Recognition.FreedomEngine.LearningMatch, TiS.Recognition.FreedomEngine.IFECandidates)
   at TiS.Recognition.FreedomEngine.FreedomEng.RunFreedom(TiS.Recognition.FreedomEngine.FFS, TiS.Recognition.FreedomEngine.FreedomConfiguration, TiS.Recognition.FreedomEngine.FreedomMatchResult ByRef)
   at TiS.RecognitionServices.FreedomService.Freedom.Run(TiS.Recognition.Common.TPage, System.Drawing.Bitmap, TiS.RecognitionServices.FreedomService.FreedomServiceConfiguration)
   at TiS.RecognitionWorkflow.Activity.Freedom.FreedomActivity+<>c__DisplayClass1.<Process>b__0(Int32, System.Drawing.Bitmap)
   at TiS.RecognitionWorkflow.Common.Drd2RegBitmaps.ForEach(System.Action`2<Int32,System.Drawing.Bitmap>)
   at TiS.RecognitionWorkflow.Activity.Freedom.FreedomActivity.Process(TiS.Core.Application.DataModel.Dynamic.ITisCollectionData, System.Activities.NativeActivityContext, TiS.RecognitionServices.FreedomService.Freedom)
   at TiS.RecognitionWorkflow.Activity.Freedom.FreedomActivity.RunService(System.Activities.NativeActivityContext, TiS.RecognitionServices.FreedomService.Freedom)
   at TiS.RecognitionWorkflow.RecognitionActivity`1[[System.__Canon, mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]].Continue(System.Activities.NativeActivityContext, System.Activities.Bookmark, System.Object)
   at System.Activities.Runtime.BookmarkCallbackWrapper.Invoke(System.Activities.NativeActivityContext, System.Activities.Bookmark, System.Object)
   at System.Activities.Runtime.BookmarkWorkItem.Execute(System.Activities.Runtime.ActivityExecutor, System.Activities.Runtime.BookmarkManager)
   at System.Activities.Runtime.ActivityExecutor.OnExecuteWorkItem(System.Activities.Runtime.WorkItem)
   at System.Activities.Runtime.Scheduler+Callbacks.ExecuteWorkItem(System.Activities.Runtime.WorkItem)
   at System.Activities.Runtime.Scheduler.OnScheduledWork(System.Object)
   at System.Runtime.Fx+SendOrPostThunk.UnhandledExceptionFrame(System.Object)
   at System.Activities.SynchronizationContextHelper+WFDefaultSynchronizationContext+<>c__DisplayClass1.<Post>b__0(System.Object)
   at System.Runtime.ActionItem+DefaultActionItem.TraceAndInvoke()
   at System.Runtime.ActionItem+DefaultActionItem.Invoke()
   at System.Runtime.ActionItem+CallbackHelper.InvokeWithoutContext(System.Object)
   at System.Runtime.IOThreadScheduler+ScheduledOverlapped.IOCallback(UInt32, UInt32, System.Threading.NativeOverlapped*)
   at System.Runtime.Fx+IOCompletionThunk.UnhandledExceptionFrame(UInt32, UInt32, System.Threading.NativeOverlapped*)
   at System.Threading._IOCompletionCallback.PerformIOCompletionCallback(UInt32, UInt32, System.Threading.NativeOverlapped*)

Has anyone seen this before? Any tips?




## **Answer / Solution** ##

If you are using FreedomDemo (5.0.3.6) then you will have this unexpected error because in the script, it has the “connection string” for learning database setting in it which does not exist for eFLOW 4.5 or maybe 5.0.2.2.  The error log is not telling you the specific issue.  So either you trigger the creation of the learning DB or remove the string.  I have a case for that as it really made others spending time trying to find the issues which is actually due to this string which does not exist in earlier version…. So Support said that will be fixed in the next version.

![](http://i.imgur.com/iMBX8Cs.png)

Next, which I cannot remember which version… there seem to have issue when your virtual engine has Omnipage engine in it (if I am not wrong then the IR virtual page engine has it).  You may want to check this out.  Remove the engine to get things going.

Last Omnipage version has a problem when Rotations are enabled in the script and the image requires a rotation. It crashes. 





