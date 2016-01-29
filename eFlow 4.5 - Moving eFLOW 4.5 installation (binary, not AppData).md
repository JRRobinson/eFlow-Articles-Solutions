# **eFlow 4.5 - Moving eFLOW 4.5 installation (binary, not AppData). ** #

## **Question / Description** ##

Did anyone ever move (without reinstalling) eFLOW installa from C drive to D drive (or other drive) ?
 
I have a request where a customer do not want eFLOW installed in C, and it is already.

Thing is that this is in cluster, meaning there are 2 servers.
 
I guess it might be possible through a combination of modification of registry + basic configuration !?

 

## **Answer / Solution** ##

Just wanted to follow up with what we finally did to move the installation from C to D drive.

I chose the "clean" approach by reinstalling and installing again.
 
Since the server is clustered I will document the procedure that worked perfectly fine:
 
1. Uninstalled clients
 
2. Clustered server 1 (the one currently active)
    a) Took eFLOW service offline through Cluster Admin tool
    b) Uninstalled eFLOW
    c) Installed eFLOW in D drive (D:\TiS\eFlow 4.5\ and D:\TiS\eFlow 4.5\AppData)
    d) Took the shared storage disk online (where AppData resides), only storage not eFLOW service
    e) Modified the following in Basic Configuration
        - SQL Server (remote in this case)
        - AppData folder, pointing to shared storage (2d was necessary to do this successfully)
        - Set cluster name accordingly
 
3. Took eFLOW service online through Cluster Admin
    - Tested that it was ok
 
4. Moved eFLOW service to server 2
 
5. Repeated steps 2 and 3 For server 2
 
6. Installed clients
 
So it was quite painless.
 
One note for the server installation: Do not try to have shared storage online and during installation set AppData folder to shared storage, does not work (I tested as you have guessed).























