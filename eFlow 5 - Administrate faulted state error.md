# **eFlow 5 - Administrate faulted state error** #

## **Question / Description** ##

I’m encountering this dreaded error for a new installation:

![](http://i.imgur.com/mTUzDgX.jpg)

-          Windows 2008 Server R2
-          Local SQL server, 2008 R2
-          Installation succeeded without any issues. Management and Monitor DBs get created automatically successfully by installation.
-          “System cryptography: Use FIPS compliant algorithms for encryption, hashing, and signing” is disabled as required.
-          “KtmRm for Distrubuted Transaction Coordinator” is started as required.
-          Tis Default STS can be browsed successfully
 
I’m trying to re-install .NET 4. Any clues?

       

## **Answer / Solution** ##

-          Basically I had eFlow 5.0.2.02 installed in this environment and working before. 
          
-          Then about a month ago, I uninstalled eFlow. The pre-requisites (.NET 4, AppFabric, etc) are still there of course. 

-          Today when I went into this environment and installed eFlow, the installation seems to be successful wherein DBs got created automatically successfully. However, I couldn’t launch Administrate even after several appool reset. This _might_ be due to missing System entry in E_App. I didn’t check at the time
-          I then re-installed .NET and AppFabric. 




