## eFlow 4.5 - No need for setWow ##

### Question/ description: ###
We have a customer in Spain who have installed an eFlow client on a CITRIX server and share the stations on this server through the CITRIX virtualization tools. The CITRIX server is x64 and the tools are x64 apps and use .NET 2 in x64.

But Flow 4.5 is an x86 platform which uses .NET 2 in x86 and that's why we run setWow.

For a standard Invoice Reader, on the client machines, setWow does not seem to be needed as the Completion station, the Module Activator and the Controller works fine without it. But if you implement a Custom station, for instance and as in our present case, setWow is mandatory.

You can all see the conflict.

### Answer: ###
Now the solution, not to have to use setWow:

- Select the x86 .exe file (let's call it "my.exe") that does not work on your x64 with .NET 2 in x64 OS
- Run the .NET tools `corflags /32bit+ my.exe`
- Replace the .exe by the modify one

You can then run Set 64 and you custom x86 should still work fine.

I hope this helps.