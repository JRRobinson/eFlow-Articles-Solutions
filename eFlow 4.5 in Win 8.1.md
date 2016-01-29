## eFlow 4.5 from SP5 onwards: DTC ##

### Question/ description: ###
I have installed eFlow 4.5 on windows 8.1. Installation was smooth with no errors but when trying to install application I get error like 'access denied' to the ProgramData directory.

I turned the UAC off and make sure all my TIS folder under AppData is not read only, but it still doesn't let me overwrite any files under those directory.

Someone have an idea how to solve it? 

### Answer: ###

The root cause were - setting up writing permissions on ProgramData\tis folder and configuration of SQL server database. 