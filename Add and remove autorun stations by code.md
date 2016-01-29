## Add and remove autorun stations by code ##

### Question / Description: ###

Is there a way to programmatically (.NET) add and remove autorun stations definition? 

The eFlowCmd.exe AutorunEntryRemove does not work, and I need the functionality of the first removing all definitions and then add again.

Sounds strange maybe but it is to be sure only the relevant definitions are added.


### Answer / Solution: ###
After some digging in CSM.

To remove all configurations:

    ITisPreconfiguredStationsGroup preConfStnGroup=m_csm.Application.Stations.Preconfigured.DefaultGroup;
	while(preConfStnGroup.Stations.Length > 0){
		ITisPreconfiguredStation preConfStation=preConfStnGroup.Stations.ElementAt(0);
		preConfStnGroup.DeleteStation(preConfStation);
	}

To add configuration (2 examples):

    ITisPreconfiguredStationsGroup preConfStnGroup = m_csm.Application.Stations.Preconfigured.DefaultGroup;
	preConfStnGroup.AddStation("Importar","efSimpleAuto.exe",string.Empty, new string[1]{"KP-TIS-WIN7"},5,true);

	preConfStnGroup.AddStation("PageOCR","efProcessShell.exe","AssemblyName:TiS.PageOCR", new string[1]{"KP-TIS-WIN7"},5,true);

at CN project we use to have a batch command script using eflowcmd executable:

    cd "E:\Program Files\TIS\eFlow 4\Bin"
    
    REM remove previous AUTORUN stations
    eFLowCmd AutorunEntryRemove iCash iCasheFlow FilePortal
    eFLowCmd AutorunEntryRemove iCash iCasheFlow EDIPortal
    eFLowCmd AutorunEntryRemove iCash iCasheFlow XMLPortal
    eFLowCmd AutorunEntryRemove iCash iCasheFlow ExportTMS
    eFLowCmd AutorunEntryRemove iCash iCasheFlow ChkReaderId
    eFLowCmd AutorunEntryRemove iCash iCasheFlow ChkRecog
    eFLowCmd AutorunEntryRemove iCash iCasheFlow FreeMatch
    eFLowCmd AutorunEntryRemove iCash iCasheFlow FreeProcess
    eFLowCmd AutorunEntryRemove iCash iCasheFlow ARMatching
    eFLowCmd AutorunEntryRemove iCash iCasheFlow FreeCollect
    eFLowCmd AutorunEntryRemove iCash iCasheFlow Clean
    
    REM Add new AUTORUN stations
    eFlowCmd AutorunEntryAdd iCash iCasheFlow FilePortal efAutogate.exe 1 "-Flow=CN_CashImaging -ns"
    eFlowCmd AutorunEntryAdd iCash iCasheFlow EDIPortal efSimpleAuto.exe 1 "-ns"
    eFlowCmd AutorunEntryAdd iCash iCasheFlow XMLPortal efSimpleAuto.exe 1 "-ns"
    eFlowCmd AutorunEntryAdd iCash iCasheFlow ExportTMS efSimpleAuto.exe 1 "-ns"
    eFlowCmd AutorunEntryAdd iCash iCasheFlow ChkReaderId efProcess 1 "-ns"
    eFlowCmd AutorunEntryAdd iCash iCasheFlow ChkRecog efProcess 1 "-ns"
    eFlowCmd AutorunEntryAdd iCash iCasheFlow FreeMatch efProcess 1 "-ns -IgnoreExtraRois"
    eFlowCmd AutorunEntryAdd iCash iCasheFlow FreeProcess efProcess 1 "-ns -IgnoreExtraRois -FieldRect"
    eFlowCmd AutorunEntryAdd iCash iCasheFlow ARMatching efSimpleAuto 1 "-ns"
    eFlowCmd AutorunEntryAdd iCash iCasheFlow FreeCollect effCollect 1 "-Mode:2 -ns"
    eFlowCmd AutorunEntryAdd iCash iCasheFlow Clean efExport 1 "-ns"

As I mentioned the remove command does not work in 4.5.1.700, I assume in other builds it does.

In this change it made sense in code anyway, since I needed other updates as well as this, only possible through coding.

OK, I didn't know about the eflowcmd not being work on 4.5. CN Project is still using 4.1.20.  Thanks for sharing the solution.