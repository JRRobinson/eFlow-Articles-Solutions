# **eFlow 4.5 SP6 - CSM Login** #

## **Question / Description** ##

I am trying to connect to the CSM from a custom station.

I am using SImpleDemo as application name and efInternal as station name.

I get an exception with the following message:
“Failed connecting to eFlow - Empty ServicesHostName (App=[System], Role=[EDC])”

There are no issues opening any eFLOW station on the machine, (controller is opening with no issues).

Any tips?


## **Answer / Solution** ##

This is a “heads up” information.

My CSM login issue was due to the target platform.

When creating a new project in .NET normally the target platform is set to “Any Platform”.

The machine I was developing on was a 64 bit machine so the exe I created was targeted according to the OS.

When it was looking in the registry for the eFLOW information it did NOT look in the 32 bit region but in the “standard” 64 entries.

Obviously, (since this is eFLOW 4.5), the eFLOW entries reside in the 32 bit section.

Once the target platform was changed to x86 the login was successful.

Thanks a lot to Eugene Reshko for all the support and help.















