# **eFlow 5 - Launching Administrate** #

## **Question / Description** ##

I’m getting this error when launching Administrate in a newly installed environment.

![](http://i.imgur.com/60wdbVB.png)



## **Answer / Solution** ##

Resolved. Grant the user access to system temp folder (from Environment Variables) and it worked.

Clarification: This is not the eFLOW AppData folder. It is the path configured as the TMP/TEMP path under system paths in Environment Variables.




