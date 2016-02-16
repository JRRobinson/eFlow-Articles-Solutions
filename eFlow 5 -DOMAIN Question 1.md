## eFlow 5 -DOMAIN Question 1 ##

### Question/ description: ###
Can we have eFlow 5 Server and clients out of an Active Directory Domain? I mean, machines that don't belong to any domain.

### Answer: ###
Amos> Yes, you could. This means machines are in workgroup or something like that. You can use SQL ID for the DB connection with TiSAppPool. If you have cross-server issue and no domain then use Network Service (NT Authority\Network Service).

You may end up using IP addresses. Please note that they must be in same network even if no domain so that they are reachable...otherwise you will need the system engineer or network engineer to help resolve the networking and connectivities, including any firewall, etc...
