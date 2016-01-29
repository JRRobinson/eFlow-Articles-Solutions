## eFlow 4.5 - New client installation ##

### Question/ description: ###
So a new 64-bit machine in Virtual Machine environment to support EDC which is having a strange problem that after installing the application completion (for example) is crashing on start up giving a common error trace like (attached the rest of the log):

Failed to resolve a node for service [TiS.Core.PlatformRuntime.DBAccess.ITIsDBAccessProxy] in application [Pirelli_Invoice]

### Answer: ###
This was due to who m ain reasins:

1. The TIS wuick module was crashing (build/ installation file issue?)
2. The FQN name must contain capital letters

Fernando checked every single module in eFlow 4.5.1.700 installed (things that I've never seen until now) and find out and fixed the firsts issue; which may affect alto the Silent installation Pirelli is trying to run with no success (we'll proceed testing again tomorrow), when tried as last try changing the domain to capital letters with success...

The reason why completion was not staring, was Tis Quick Service, at the client side, was not being instantiated successfully.

A shutdown of the eflowdmn.exe on the client side and an unregister station from Enterprise Manager did the trick.

[https://app.box.com/s/92g0gw0un9o9p6ab7alk](https://app.box.com/s/92g0gw0un9o9p6ab7alk)

Although I've made the FQN all upper case, I think the casing does not matter at all, but David can double check this when he fixes the remaining machines.

My feeling was that such machine was registered already when the new cab was deployed and for some reason the service was not refreshed and kept failing,
See below the type of service I am talking about.

[https://app.box.com/s/ihz0e64ohtpoq9o7voxy](https://app.box.com/s/ihz0e64ohtpoq9o7voxy)