# **eFlow 5.2.0.10 - Enterprise Manager remains in splash screen** #

## **Question / Description** ##

I am facing a strange behavior on eFlow 5.2.0.10 with all the modules.  This is the scenario:

After a fresh installation I had the chance to open Enterprise Manager, install the license and the SimpleDemo application, and run a batch through all the flow. No issues at all.

I restarted the VM (Windows 10) and after that all the modules, for instance Enterprise Manager and Control, start but the application does not open, the splash screen remains on the screen and the application keep consuming 99%  of CPU.

No errors are recorded into TIS_Log even if I kill the session…

Now, if I reinstall (removing and installing the whole thing) eFLOW works again, but if I reboot the VM, the problem come back.

No clue about what’s happening... anyone had  this problem as well?

## **Answer / Solution** ##

I’d check the certificates. Check if you can still browse the services, etc.

If you’re using HTTPS, try a new self-signed certificate. Also, [http://documentation.topimagesystems.com/index.php?option=com_k2&view=item&id=30](http://documentation.topimagesystems.com/index.php?option=com_k2&view=item&id=30)

I had to reinstall the certificates to put them to work again… I rebooted the machine (just to be sure the certificates were well installed) and now I can open the EM successfully!

