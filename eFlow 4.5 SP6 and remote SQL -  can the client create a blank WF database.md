## eFlow 4.5 SP6 and remote SQL -  can the client create a "blank" WF database ##

### Question/ description: ###

For this first time application installation, can the client create a "blank" WF database and then install via Enterprise Manager? 

### Answer: ###
Yes, the best way to do it is to create the WF script on a different machine (in order to include all the application settings like queue ids, meta tags, ...) and the to install it in the remote SQL.