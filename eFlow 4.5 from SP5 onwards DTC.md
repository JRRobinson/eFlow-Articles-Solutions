## eFlow 4.5 from SP5 onwards: DTC ##

### Question/ description: ###
Problems with DTC Communication from SP5 onwards what is the cause?

### Answer: ###

An eFlow 4.5 SP6 installation was not able to add AutoRun Stations or add another application. The problem was the firewall was blocking port 135. TYhis port is used for DTC communication and must be free. If it is blocked transactions are not properly send as they are blocked. But there are secondary ports to be blocked as well. in a standard OS installation this would be port 5000-5020 (standard installation, as this range can be changed in the Registry).

See this link for more information:
[http://support.microsoft.com/kb/250367/en-US](http://support.microsoft.com/kb/250367/en-US)