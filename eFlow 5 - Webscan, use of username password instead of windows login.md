# **eFlow 5 - Webscan, use of username password instead of windows login** #

## **Question / Description** ##

For the webscan: how do we set it up such that we can use username+pwd instead of the windows login?

I remember there was some setting in an xml file that took care of this, but I forgot what it was, and where I could find it



## **Answer / Solution** ##

From my portal case which I enquired how to use Windows login as SSO.

•	You will need to remark (comment out) the following section from the Web.config in the WebValidate folder: 

 authentication mode="Forms"

 forms loginUrl="~/Management/Login" timeout="2880" /
 
/authentication 

Don't forget to stop TisAppPool before so you will be able to change the file.

So to use back username password then I supposed you have to reverse the change or use back the original Web.Config (see below)
 
![](http://i.imgur.com/grkvyMF.jpg)















