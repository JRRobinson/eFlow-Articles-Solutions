# **eFlow 5 - changing assembly version** #

## **Question / Description** ##

How to change the assembly version?


## **Answer / Solution** ##

As you know we currently have a fixed assembly version for all eflow5 dlls and exe which is 5.0.0.0. The only version that is changing is the file version. 

Although this is great in preventing recompilations of dlls this actually makes the life of R&D and Support very hard when trying to analyze memory dumps, logs and crash reports. 

This is especially important in eflow 5 because we have automatic error reporting capabilities where is a process crashes for any reason you are asked if you want to send a report and the crash minidump is sent to us automatically (and yes we actually go through these reports and fix the issues). 

Problem is that we only see assembly version and not file version in the report so it’s hard for us to know if this is an old issue that was fixed or something new that we missed. 
 
Because of that we are thinking of changing the assembly version of eFLOW 5 from the next release onwards (5.0.3.X) 
Since we don’t want you to recompile your dlls with every patch/version we will also add a redirect section in the configuration of each exe. You are already using this configuration to connect to eFLOW server because that’s where the wcf configuration is located. 

You can read more about assembly redirect here:
[http://msdn.microsoft.com/en-us/library/7wd6ex19(v=vs.110).aspx](http://msdn.microsoft.com/en-us/library/7wd6ex19(v=vs.110).aspx)
 
this means that when patching a system you will also have to change this config. We will create a default configuration for each version so basically this means that you will just have to copy paste (worst case). 





