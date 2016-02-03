# **eFlow 5 - License issue after migrating a VM** #

## **Question / Description** ##

After migrating a virtual machine from VMWare to Oracle, I first could not start Controller due to invalid license.
Then I deactivated the old, got a new license, activated it and it seems to work fine.
 
Anyway I get the following warning/error in the Administrate/License Management:

![](http://i.imgur.com/WuQw3uE.jpg)

“………Local server … must be deactivated due to invalid server code…………”
 
Is this a known issue? Any hint appreciated.



## **Answer / Solution** ##

Fixed in SP1

Just uninstall the license and delete the server from the license manager (right click on the server name and remove).

Restart iis and install the license.





