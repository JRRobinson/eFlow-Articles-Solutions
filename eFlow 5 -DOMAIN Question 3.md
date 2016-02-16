## eFlow 5 -DOMAIN Question 3 ##

### Question/ description: ###
Which Ports I need to ask the administrator to allow eFlow 5 communications between Servers and Clients?

### Answer: ###
Amos> The ports used by eFlow transmission, configurable. But the most challenging is the MSDTC. Other than then known default port for MSDTC, some systems (depending on the OS), you need to rake care of dynamic high port numbers which MSDTC would use otherwise you need to edit the registry for specific port for MSDTC. YOU may also need UDP port if you have host name and other challenges. It still goes into your customer environment.