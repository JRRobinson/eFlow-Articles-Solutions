# **eFlow 5 - Roles and Security** #

## **Question / Description** ##

I am trying to set User and Supervisor role in Visual Designer and use it (same name) in DomainSecurity.xml.  Tested with 5.0.2.2 and 5.0.3.6 (recent release).  Tried several scenario, it just does not work for defined role in the application and only work for Administrator role.   Maybe I missed out something or there is really a bug somewhere.  FYI: I had logged the case 00018525.

Some key points I tried below for your reference/info

•	I recalled that someone who attended the training by Marlon, highlighted to me that if you add a user to the DomainSecurity.xml, you must also add the same user to the section where AppName=”System” other than AppName=”” or AppName=”YourAppName”.  What is the rationale?

•	Then Documentation.Topimagesystems.com talked about AppName=”” applies to all applications for the user with the role if you set it there…. otherwise you should set AppName=”YourApplicationName”.  It seems that if your defined AppName is not found there then it will go to AppName=””.

•	I have even tried to verify using user without domain and machine name, add to UserIds.xml then when the login pop-up appears at launching station (for eFLOW 5.0.3.6 when I set none of the users to be valid or not having Administrator role), I can enter the ID and password from UsersId.xml.  Still as long as it is my defined role, it does not work.  As long as you set the Administrator role, it allows you to launch every station.

I am clueless.  I needed to set this up for a project UAT and pre-test verification for roles and AD groups.  Any pointer and help is greatly appreciated.  Thanks in advance.


## **Answer / Solution** ##

I guess I can conclude the below (maybe to write an article about it) based on 5.0.3.6.
 
1.      You must define the role in visual designer as in eFLOW 4.5, follow the same approach.
2.      The user defined must be defined in AppName=”System” and the role MUST ONLY be “Administrator”.  If you change it then it will not work.  I don’t understand why.
3.      However if you are going to use Group Name (in my example using tisdomain\ sTiS-All-InlooxDBAccess AD group) then you do not need to define it under AppName=”System”.
4.      Remember that every change that you saved, you must restart TiSAppPool for the change to take effect (same for DomainSecurity.xml).  Recommended to stop TiSAppPool before you edit the xml.
5.      Behaviour of AppName=”” vs AppName=”eF5_SimpleDemo” (my example of my application name).
a.      System will look into your application setting first i.e. AppName=”eF5_SimpleDemo” in my example.
b.      If system cannot find the user in your application then it will look for the user in AppName=””.  Wherever the user was found, the role defined will be applied.
c.      AD group as “user” is 2nd priority, if you define the group in your application with a role but your specific user ID is found in AppName=”” then it will take priority for user over AD group.
d.      When you define AD group then you MUST NOT use domain name.  I don’t understand why.
                                                    i.     E.g. <UserAndRoles Name="sTiS-All-InlooxDBAccess" IsGroupName="true"> is correct.  If IsGroupName=”false” then it will not work, however in 5.0.2.2, it does not seem to matter for this value.
e.      If the role you defined in the xml is not defined in the application then it is as good as No Access Rights.
 
What may not be concluded but based on my test for using users defined in UserIds.xml, is as below

1.      Make sure that your domain ID is not defined under AppName=”System” but define your user name set in UserIds.xml to be under AppName=”System” and give it role = Administrator.

2.      Make sure that this user ID is define either at AppName = “” or AppName=”YourApplicationName”, behaviour is similar as described above.
     
3.      For the 1st time, then system based on your domain and login, it cannot find it at DomainSecurity.xml, so a pop-up UI will appear below.

 ![](http://i.imgur.com/kYMyLMT.jpg)

4.      Next, enter the user ID and password you had set in UserIds.xml but make sure that this User ID was defined under AppName = “” or AppName=”YourApplicationName” where a valid role was assigned.
     
5.      Then station launched as per normal.
     
6.      It seems that it cached this user login because the next time, this UI does not appear anymore.
 
 
About Controller:

1.      Another discovery, if you set Read Only for Controller then after launch, you can still see all the options but click it e.g. Hold Collection, the difference is nothing happened, drag the collection to other station, nothing happened.  TIS_LOG then you may see the error about permission.  Maybe this is a bug as the options should be all grey out.
 
2.      Another strange issue is sometimes, without the access right especially using login from UserIds.xml, Controller can be launched but it throws error about workflow so you see Controller UI and no workflow (station and collections).











