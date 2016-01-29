# **eFlow 5 - AppFabric 1.1:Install Error** #

## **Question / Description** ##

I uninstall AppFabric 1.1, and I have the installation again.
However, MSI installer is returned with an error code 1603.

2014-09-09 13:19:48, Information           Setup  Process.Start: C:\Windows\system32\msiexec.exe /quiet /norestart /i "c:\fb00ed73b6caf6a878d80bd4\Packages\AppFabric-1.1-for-Windows-Server-64.msi" ADDDEFAULT=Worker,WorkerAdmin,CacheClient,Setup /l*vx "C:\Users\Administrator\AppData\Local\Temp\AppServerSetup1_1(2014-09-09 13-19-48).log" LOGFILE="C:\Users\Administrator\AppData\Local\Temp\AppServerSetup1_1_CustomActions(2014-09-09 13-19-48).log" INSTALLDIR="C:\Program Files\Windows Server AppFabric 1.1" LANGID=ja-JP
2014-09-09 13:20:39, Information           Setup  Process.ExitCode: 0x00000643
2014-09-09 13:20:39, Error                 Setup  Since the MSI installer is returned with an error code 1603, installation of AppFabric failed.

## **Answer / Solution** ##

It's common AppFabric problem, hard to solve though and takes few things to do.
Most comprehensive guide I found so far is here:

[http://blogs.technet.com/b/praveenh/archive/2013/02/22/sharepoint-2013-prerequisites-fails-with-msi-installer-error-code-1603-while-installing-appfabric-1-1.aspx](http://blogs.technet.com/b/praveenh/archive/2013/02/22/sharepoint-2013-prerequisites-fails-with-msi-installer-error-code-1603-while-installing-appfabric-1-1.aspx)





