## eFlow 4.5 SP6 and remote SQL -  matching paths ##

### Question/ description: ###
Does it still required to have matching paths in the SQL server and the eFlow server for the mdf files?

### Answer: ###
Yes, it is still needed. You can use different paths by installing the databases manually and then to connect to eFlow.

What do you means "connect them to eFlow?" You mean install DB manually to avoid eFlow installing the DB?

Exactly, if the databases are already there so no need to create the path since the connection string will work anyway.