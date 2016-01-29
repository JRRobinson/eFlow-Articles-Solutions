# **eFlow 4.5 - Bat file for restarting autorun ** #

## **Question / Description** ##

Has anyone has prepared a bat file for restarting eFlow autorun?


## **Answer / Solution** ##

@ECHO OFF

NET START | FIND /I "T.i.S. eFlow Daemon" >NUL
 
IF NOT ERRORLEVEL 1 GOTO ISGOOD

GOTO START
 
:START

NET START "T.i.S. eFlow Daemon"

GOTO ENDE
 
:ISGOOD

NET STOP "T.i.S. eFlow Daemon"

PAUSE

NET START "T.i.S. eFlow Daemon"

GOTO ENDE
 
:ENDE

PAUSE





















