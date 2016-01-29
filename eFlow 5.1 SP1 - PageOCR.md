# **eFlow 5.1 SP1 - PageOCR** #

## **Question / Description** ##

I’m getting this error when running pageOCR (OCE/Expervision) on some images:
2015-03-11 16:37:48,874 [15] ERROR Source App: efProcessShell.exe, Message: TiS.Core.TisCommon.TisException: Failed Tip operation. RC = 2
   at TiS.RecognitionServices.FullPageOCRService.FullPageOCRService.HandleTipServiceResourceCode(Int32 rc, Int32 fileId)
   at TiS.RecognitionServices.FullPageOCRService.FullPageOCRService.CreateTifFileHandles(ITisFullPageOCRConfig ocrParams, String tifFullPath, String targetTifFullPath, Int32& sourceTifFileId, Int32& targetTifFileId)
   at TiS.RecognitionServices.FullPageOCRService.FullPageOCRService.RunCollection(ITisCollectionData collectionData, ITisFullPageOCRConfig ocrParams, Func`2 validPage)
   at TiS.RecognitionWorkflow.Activity.PageOCR.PageOCRActivity.RunService(NativeActivityContext context, FullPageOCRService pageOcrService)
   at TiS.RecognitionWorkflow.RecognitionActivity`1.Continue(NativeActivityContext context, Bookmark bookmark, Object obj)
   at System.Activities.Runtime.BookmarkCallbackWrapper.Invoke(NativeActivityContext context, Bookmark bookmark, Object value)
   at System.Activities.Runtime.BookmarkWorkItem.Execute(ActivityExecutor executor, BookmarkManager bookmarkManager)

Anyone encountered this before?


## **Answer / Solution** ##

Found the root cause.

I was using ePortal to import these PDFs. The PDFs’ names contains a couple of dots (‘.’).

I can still View Collection from Control. TIF is present in dynamic file.

I’ll log a bug later for this. eFlow should either:
-	Prevent importing files with invalid name or
-	Import and process it successfully all the way through.

