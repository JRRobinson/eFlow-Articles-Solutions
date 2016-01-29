# **eFlow 4.5 SP6 -Kadmos** #

## **Question / Description** ##

I am onsite and was reported recognition issue causing freezing of the station.

I was checking engines and by elimination came to the conclusion that it is Kadmos to be blamed, since no error was given to any log.

It is painful to the Client since they have to find and rescan blocking collections.

I found on FTP in folder HotFix Kadmos.zip file. 
I had small hope that it can corresponds to my problem, however, simple replacement of the OCR Kadmos folders gave me other error. 

Any suggestions except of removing Kadmos from VE?

eFLOW 4.5.2.256
 
  
![](http://i.imgur.com/dlmH2Vv.jpg)          

## **Answer / Solution** ##

My main problems were fast solved due to help of Alon, by adding mask to Kadmos engines.


I left with few cases which were giving similar problems but error to the log as follows:

“Faulting application efProcess.exe, version 4.5.2.264, time stamp 0x2a425e19, faulting module ntdll.dll, version 6.0.6002.19346, time stamp 0x55024102, exception code 0xc0000005, fault offset 0x0003fde5, process id 0x86c, application start time 0x01d09206cb7a7ad8.”

I was investigating why it happens for some forms while does not for others and came to the conclusion that forms to be blamed did not have EFI property Registration and BadMarings checked.

I am not yet sure what is the connection between this properties and the error, however, as fast “fix” to process problematic collections it helped. 

![](http://i.imgur.com/NqAZtXI.jpg)

