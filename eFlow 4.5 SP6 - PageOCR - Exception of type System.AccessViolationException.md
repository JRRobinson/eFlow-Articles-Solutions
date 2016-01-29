## eFlow 4.5 SP6 - PageOCR - Exception of type System.AccessViolationException ##

### Question/ description: ###
I'm facing an issue with PageOCR station. I was doing some test for a demo and after processing some collections with successful ow suddenly stopped.

eFlow 4.5 SP6

efProcessShell.exe (Page OCR)

    Exception of type System.AccessViolationException [Attempted to read or write protected memory. This often an indication that other memory is corrupt]

### Answer: ###
The issue was caused by Omni engine. I removed and worked fine. But Rotem told me the correct sequence installation:

- eFlow Path: ../Eflow/4.5_SP6/7zip/ [FTP]
- OCR Path : ../Eflow/OCRs 4.5/OCRs 4.5 Installation_SP6_HotFix.rar [FTP]
- Remove read only attribute of: ..\eFlow4.5\OCRs\ScanSoft\TIS_Nuance_19.lcz

Now I can use Omni engine without problems.

Many thanks to Rotem, Robson, Fernando, Ofir and Amos!