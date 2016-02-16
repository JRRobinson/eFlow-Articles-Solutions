# **eFlow 5 - Controller not showing the workflow** #

## **Question / Description** ##

I have a pretty strange problem with the new eFlow 5 installation by the customer. Advanced demo application is working normally if I run all stations in the workflow order (File Portal, then Form Id etc.). Collection gets processed without errors through all stations. But Controller will never show any change, actually it will not show even the workflow (see the screenshot below).

Launch Pro will also not show any change, including after click on Refresh. I have the same issue on my local virtual machine, so it’s not just in one environment. 

I tried with SimpleDemo and one of my applications which is normally working on other machine. Permissions, UAC, firewall turn-off, configuration.xml or domainsecurity.xml – nothing changes this behaviour. 
 
Any ideas?

![](http://i.imgur.com/FGIMhgg.jpg)

## **Answer / Solution** ##

. It was actually the part of a bigger problem with not having the filestream functionality enabled on the SQL Server level. 
 
eFlow 5 installation assumes that Filestream option on SQL Server is enabled. However, customer was complaining why this feature has to be enabled just because of eFlow, especially in case when the same SQL Server supports lot of their other application (note that after enabling filestream, SQL Server must be restarted). 
 
Thanks to Rotem, I succeeded to install eFlow 5 without filestream, but this has to be done with special procedure which includes manual running of several SQL scripts directly on SQL Server. I wrote down the description of this procedure. If any of you will ever need it, he can contact me any time. 

 





