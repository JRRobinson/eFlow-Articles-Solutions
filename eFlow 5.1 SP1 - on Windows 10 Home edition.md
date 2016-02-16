# **eFlow 5.1 SP1 - on Windows 10 Home edition** #

## **Question / Description** ##

A partner asked me to install Eflow 5.1 SP1 on a Windows 10 Home Edition.

I got a advise from Alon (thanks Alon) that one of the possible issues would be during the installation there will be a message about “II 7.0 or above is not installed”. This happens because Windows 10 comes with IIS 10. The workaround suggested by Alon works fine:

Error message during eflow installation: “II 7.0 or above is not installed”.

Workaround:

“Go to registry (using regedit) HKLM\SYSTEM\CurrentControlSet\Services\W3SVC\Parameters\ and change the paramter MajorVersion to 7. Do the eflow installation and change it back to A  (10 in hexa).”

With the trick above, I could install Eflow 5  and SP1 + hotfixes. Before install eflow, I have enabled IIS on the Windows 10 and have installed SQL 2012 express too, configured as always, but I am not succeeding to have the Eflow databases created, and not succeed to pass the login/password screen.

When I open in the browser http://localhost:55222/eflow_5/  it shows the contents.

But when try to open http://localhost:55222/eFlow_5/DomainManagementServer.svc  it says it is missing the directory c:\inetpub\wwwroot\Tis Web Site\eFlow_5 or don´t have permission.

I have checked and confirmed the TISAppPool user has full control over this directory and over appdata.

I don´t know what to do more. If you have suggestions, please let me know.

I don´t know if the problems are because it is a Home edition of Window 2010, or if it is because it a standalone notebook, in a WORKGROUP not a domain.

After many changes and tries, now I am stuck in these messages below. I have already removed all certificates and reinstalled all of them using the command lines from 

[http://documentation.topimagesystems.com/index.php?option=com_k2&view=item&id=30:installing-eflow-certificates](http://http://documentation.topimagesystems.com/index.php?option=com_k2&view=item&id=30:installing-eflow-certificates) but no luck.

If you have overpassed the messages below, please let me  know how.

The messages appear in the browser when I try to test the webservice calling

http://machinename:55222/eFlow_5/DomainManagementServer.svc 
And the database are still not being created.


## **Answer / Solution** ##

The problem was MSDTC not configured properly. When during the installation we do a Validate of the prerequisites, it shows quickly some items on the list saying it is ok, and allow us to continue the installation, but in fact it should not allow us to continue, since the validation of other items are still happening. After almost one minute, it shows that other items are ok and at the end showed me the MSDTC was not configured properly (first time I did the installation I did not notice this and continue before to finish the validate.

Now DBs were created

