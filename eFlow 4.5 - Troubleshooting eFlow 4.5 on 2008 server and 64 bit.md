## eFlow 4.5 - Troubleshooting eFlow 4.5 on 2008 server and 64 bit ##

### Question/ description: ###
Odd issues such as a grey tray and unresponsive eFlow modules could be seen when running eFlow 4.5

Symptoms: Grayed out eFlow tray and unresponsive (crashing) eFlow station modules.

### Answer: ###

Cause: initial testing indicates that when the system enables IPV6 (which is enabled by default on Windows Vista and Windows 2008 Server 64 Bits) eFlow uses the supplied IPV6 address, which causes a failure during connect causing the tray to be grayed out.

Solution
There are two possibilities. One is to edit the current SystemData.TISXML file and try to replace the :1 IP address with the current IPv6 IP address. In order to this eFlow Service needs to be turned off. Another possibility consists in disabling the IPv6 protocol entirely.

Further to this it is important that when eFlow runs on a 64-bit machine it must run in virtual mode, i.e., the process actually runs in 32-bit virtual mode inside the 64-bit space. in order to achieve this you must run the ldr64.exe utility and setting it to load .NET assemblies as 32-bit processes.

For further details please refer to the eFlow 4.5 release Notes.


1. Before running eFlow service, go to the command prompt to the path C:\WINDOWS\microsoft.net\Framework64\v2.0.50727 
2. Run the command: ldr64 setwow