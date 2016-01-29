## eFlow 4.5 SP6 and remote SQL -  delete/ create the WF DB ##

### Question/ description: ###

Will eFlow try to delete/ create the WF DB when I override  an application?

### Answer: ###
Yes, eFlow reinstall the database.
if the mdf files are not in the same path..what eFlow do? reuse the existing mdf?
eFlow doesn't need the mdf files, the communication is against the SQL server.