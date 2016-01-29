# **eFlow 4.5 - AutoRun definition stored in cab? ** #

## **Question / Description** ##

Is somehow the definition of autoruns stored in a backuped cab file?

After reinstallation of cab the autoruns are lost and they haven’t got saved/exported upfront.


## **Answer / Solution** ##

You could create a script that would call eFlowCmd.exe AutorunEntryAdd to add stations after reinstalling the app.


You can create a script like the one below, that uses eflowCmd. The Autorun information is not in the CAB. In Eflow 4.5 they were written to systemdata file and in Eflow 5, they are written to a database table called E_PreconfiguredStation.

cd "C:\Program Files (x86)\TIS\eFlow 5\Bin"

eFlowCmd AutorunEntryAdd iCash iCasheFlow FilePortal efAutogate.exe 1 -Flow=CN_CashImaging

eFlowCmd AutorunEntryAdd iCash iCasheFlow EDIPortal efSimpleAuto.exe 1

eFlowCmd AutorunEntryAdd iCash iCasheFlow XMLPortal efSimpleAuto.exe 1

eFlowCmd AutorunEntryAdd iCash iCasheFlow ExportTMS efSimpleAuto.exe 1

eFlowCmd AutorunEntryAdd iCash iCasheFlow ChkReaderId efProcess 1

eFlowCmd AutorunEntryAdd iCash iCasheFlow ChkRecog efProcess 1

eFlowCmd AutorunEntryAdd iCash iCasheFlow FreeMatch efProcess 1

eFlowCmd AutorunEntryAdd iCash iCasheFlow FreeProcess efProcess 1

eFlowCmd AutorunEntryAdd iCash iCasheFlow ARMatching efSimpleAuto 1

eFlowCmd AutorunEntryAdd iCash iCasheFlow FreeCollect effCollect 1 -Mode:2

eFlowCmd AutorunEntryAdd iCash iCasheFlow Clean efExport 1

Syntax of EflowCmd

eFlowCmd <AutorunEntryAdd> <Application name> <NodeName> <StationName> <ExeName>  <Count> [CommandLine]




















