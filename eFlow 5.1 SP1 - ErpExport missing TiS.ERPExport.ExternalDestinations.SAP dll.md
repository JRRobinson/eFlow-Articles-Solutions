# **eFlow 5.1 SP1 - ErpExport missing TiS.ERPExport.ExternalDestinations.SAP.dll** #

### **Question/Description:** ###

Creating a new SAP Destination from ERPExport and after selecting the SAP Destination Port I got this error:

System.Exception: Problem occured while instantiating the configured external destination. ---> System.IO.FileNotFoundException: Could not load file or assembly 'TiS.ERPExport.ExternalDestinations.SAP' or one of its dependencies. The system cannot find the file specified.

As a matter of fact the required dll is not present under the bin folder
TiS.ERPExport.ExternalDestinations.SAP.dll.  
I also searched the installation package for eFlow 5.1 and SP1 and the dll is not there.
Under eflow 4.5 bin the file exists.

### **Answer/Solution:** ###

In eFlow 5 it moved to TiS.ERPExport.ExternalDestinations.SAP.Common.dll 
You need to change in ERPExportSetup.xml and refer to this assembly from here:
<ExternalDestinationMapping extensionClass="TiS.ERPExport.ExternalDestinations.SAP.SAPExternalDestination, TiS.ERPExport.ExternalDestinations.SAP.Common" name="SAP" type="ERP" />

