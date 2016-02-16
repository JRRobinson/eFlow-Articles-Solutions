## eFlow 5 - AppFabric example ##

### Question/ description: ###
Maybe let's do it on an example.

Production environment, 1 server, 1 worker, SQL on separate machine.

AppFabric installed on a server.

What is the benefit of enabling AppFabric and what section should be enabled (I remember there were 3, one them was cluster?)

### Answer: ###
eFlow is running in stateless mode in IIS this means that things like configurations and sessions state should be stored somewhere. 

We are using AppFabric for the caching in that case.

This means that if you are using AppFabric caching and the IIS restarts/ crash, nothing bad happens to sessions that are running.

If you are not using it then the stations will need to be restarted.

