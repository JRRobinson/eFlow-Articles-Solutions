# **How to Backup the log file using a Batch File** #

## **Question / Description** ##

To automatically make a backup of eFlow logs files - useful for customers. 

## **Answer / Solution** ##

@echo on
SETLOCAL EnableDelayedExpansion
@echo Backing Up eFlow Log.txt 
 
set MYDATE=%DATE:~10,4%%DATE:~7,2%%DATE:~4,2%
set COMP="%PROGRAMFILES%\7-zip\7z.exe"
 
set backupRootFolder=E:\TIS\eFlow 4.5\AppData\Log\LogBackups
set logFolder=E:\TIS\eFlow 4.5\AppData\Log
 
mkdir "%backupRootFolder%\%MYDATE%"
 
move "%logFolder%\Log.txt" "%backupRootFolder%\%MYDATE%"
copy "%backupRootFolder%\%MYDATE%\Log.txt" "%backupRootFolder%\%MYDATE%\Log_%TIME:~0,2%%TIME:~3,2%.txt"
del "%backupRootFolder%\%MYDATE%\Log.txt"
cd %backupRootFolder%\%MYDATE%
%COMP% a -t7z %FORMAT% "%backupRootFolder%\%MYDATE%\%MYDATE%.7z" "%backupRootFolder%\%MYDATE%\Log_%TIME:~0,2%%TIME:~3,2%.txt"
del "%backupRootFolder%\%MYDATE%\Log_%TIME:~0,2%%TIME:~3,2%.txt"






