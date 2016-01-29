# **eFLOW 4.5 - Station Startup Issues ** #

## **Question / Description** ##

We have a 4.5 SP2 server that seems to always run stations in foreground rather than background mode when started from the controller. It seems to do this for all applications and whether logged in as a local or domain account.
 
They do still seem to show as running under NT AUTHORITY\SYSTEM rather than the user.
 
Do you have any idea what might cause this? It’s nothing urgent as it’s only a test server but just means we have to keep a session logged in is all which can be a bit of a pain.



## **Answer / Solution** ##

Do you have on the eFlow service on that machine the option "Allow service to interact with Desktop" checked / ticked?

Looks like it was checked before, I unchecked, restarted the service and now they are starting in the background.


----------
First, this is not the default behavior of a service and should never be checked/ticked, but I’ve seen a wave of machines having this checked lately, so I want to give a heads up here…

Just some background information why it should not be ticked/Checked

This has caused issues on servers when stopping autoruns or trying to restart the server remotely as sometimes the stations are interacting with the desktop crash it. Since it is a server where no one is connected there is no way of restarting them besides logging into the machine.

I had even cases where the only way was a hard reset, due to many instances taking the whole CPU and login was impossible.

Another issue I see, is when allowing the service to interact with the desktop, eflow starts throwing pop up messages on servers that no one is there to see, instead of logging it into the logger.

This is not really acceptable in production environments. 

IMHO it should never be checked. This is a service designed to run in background.  Never to interact with the desktop.

So in order to have a standard way*  of configuring the “Tis Eflow Daemon” please never check “Allow service to interact with Desktop” . It is unchecked by default.


*I know I say the word standard too many times, but it is for a good reason, in order to allow everyone to get some sleep when it is most important ;)































