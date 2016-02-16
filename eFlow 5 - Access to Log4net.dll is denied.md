## eFlow 5 - Access to Log4net.dll is denied ##

### Question/ description: ###
I'm not able to start a Completion because of following:

    Login failed. ExceptionMessage: Application login [OCCS] as station [Maker] failed, Access to the path 'C:\ProgramData\TIS\eFlow 5\AppData\Client\OCCS\Customization\log4net.dll' is denied
    
Does anyone know how to fix it?

eFlow 5.0.3 (no SP)

### Answer: ###

Delete all files under Customization folder then it works.