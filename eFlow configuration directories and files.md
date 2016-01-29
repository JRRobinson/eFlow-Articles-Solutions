# **eFlow configuration directories / files** #

## **Question / Description** ##

Can someone explain the difference between these 2 directories:

C:\inetpub\wwwroot\Tis Web Site\TisDefaultSTS\Bin\ConfigSources

C:\inetpub\wwwroot\Tis Web Site\eFlow_5\Bin\ConfigSources

Why we need to change the TISConfiguration.config in both of the directories above? Why not only one directory? A customer is asking me why we need to change on both and I could not find the reason.


## **Answer / Solution** ##

These are the WCF configuration files for the 'Server'.
eFlow 5 has two server applications, the Real Thing (eFlow 5, basically what you knew as eFlowDmn in previous releases) and the STS/Claims Service. The latter hands out encrypted data containing your claims, your .. permissions. The former is everything from 'install application' to 'GetCollection'.

Why two directories? I can only guess that this is caused by WCF / .Net forcing us to use relative paths in the web (or app) config file, so 'bin\ConfigSources\Foo.xml' is allowed, 'C:\inetpub\wwwroot\Tis Web Site\ConfigSources\Foo.xml' (aka a shared place) isn't. I wouldn't know if you _could_ traverse up using something like '..\..\..\' etc.

Plus,since I don't think we support any version of Windows that doesn't require a NTFS system drive, it might be trivial to just use mklink /J to create a junction between those directories.
That way, changes in one place would effect the other as well.

Does it matter though, in the end? Why do you change those files manually – and how often?


----------

Benjamin, thanks for the explanation. You are right, we don´t need to change this file frequently, usually only one time. But we need to know how to answer a customer question when it comes, and not only say “it is because it is”. Sounds  crazy to change in 2 places. Maybe we should have a tool (if we have let me know) we could use to configure eFLOW without need to change files directly.




















