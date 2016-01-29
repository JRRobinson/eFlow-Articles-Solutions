# **eFLOW 4.5 - FilePortal issue with lower case tif extension ** #

## **Question / Description** ##

A customer has a problem with the import of files with lower case extension (*.tif). The logger shows the following, severity Info:
 
**PixTypeConvertor.ConvertTypeNameToExtension:Type [tif] is not a valid PixFileType**
 
In this case the file does not even appear in “Files in process” list. If I rename the same file in *.TIF it works nice and smooth.
 
 
Note: on my machine, same application, I get the same message in the logger, but the image is correctly processed.

## **Answer / Solution** ##

Yes, because the eFlow build that the customer is using is likely a different build than yours.
 
4.5.1.X builds include a different version of the PixTools runtimes and 4.5.2.X builds. Actually even within 4.5.1.X builds there are some slight differences with the PixTools runtimes.
 
I would just add a C# routine on the OnFileRead or similar event to uppercase the extension name of the file being imported.




























