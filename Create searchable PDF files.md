# **Create searchable PDF files** #

## **Question / Description** ##

Customer Allianz asked me if we can create searchable PDF files with eFlow.

Ulrike told me this should work with ERP Export.
 
Has anybody experience with this and can give me a description how to do it and what we need for it (additional tools, …)?



## **Answer / Solution** ##

All you need is the itextsharp-based plugin developed by Ben
git@git.topimagesystems.com:pdfconverter/pdfconverter.git
 
Get it, replace itextsharp.dll in your bin with the one you will find in the repository above.
Compile the sources, run ERPExportPluginScan.exe (eFlow 4.5, probably not needed in 5.0).
 
Then when you start ERPExport you will find it in Configuration

![](http://i.imgur.com/xGqEwD0.png)


----------

the standard approach ( no code / no compile) 
 
How to setup searchable pdf conversion
 
Instructions:
 
Download the latest Invoice Reader form the ftp for the version you want. 4.1 or 4.5
 
Extract the PDF-A-Stuff.zip that is under “BinEtc\eFBin\Utilities” into the bin
 
Add an entry in your ERPExportsetup and the rest should be pretty straight fwd
 
Add a new ConverterMapping-Entry into your ERPExportSetup.xml
 
<ConverterMapping extensionClass="TiS.ERPExport.ImageConversions.PDFConverterPlugin, TiS.ERPExport.ImageConversions.PDFConverter" name="PDFA" />

![](http://i.imgur.com/Q86XM4e.jpg)


Add a new Attachment-Tag into your ERPExportSetup.xml or select the conversion directly inside the ERPExport-Configuration GUI
 
<Attachment attachmentType="TIF" exportFormPagesOnly="False" conversionCode="PDFA:SearchablePDFA" merge="False" />

![](http://i.imgur.com/ehQG12J.jpg)


----------

There is no automatic plugin scanning in eFlow 5.
So you need to add this line manually into ERPExportSetup.xml to be able to select the plugin in GUI:
 
    <ConvertersMappings extensionInterface="TiS.ERPExport.ImageConversions.IConverter">
      <ConverterMapping extensionClass="TiS.ERPExport.ImageConversions.ISEDQuickPDFConverterWrapper, TiS.ERPExport.ImageConversions" name="iSEDQuick" />
      <ConverterMapping extensionClass="TiS.ERPExport.ImageConversions.LeadTOOLsConverterWrapper, TiS.ERPExport.ImageConversions" name="LeadTOOLs" />
      <ConverterMapping extensionClass="TiS.ERPExport.ImageConversions.iTextSharpConverterWrapper, TiS.ERPExport.ImageConversions" name="iTextSharp" />
      <ConverterMapping extensionClass="TiS.ERPExport.ImageConversions.PDFConverterPlugin, TiS.ERPExport.ImageConversions.PDFConverter" name="iTextSharpTIS" />
    </ConvertersMappings>














