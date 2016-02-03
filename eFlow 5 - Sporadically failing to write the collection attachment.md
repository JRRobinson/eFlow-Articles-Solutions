# **eFlow 5 - Sporadically failing to write the collection attachment** #

## **Question / Description** ##

I have the following problem. The testing team of the customer runs a test which imports 100 emails. Every time 8-15 from these emails can’t be imported due to an exception
related to the collection creation process. 
By adding the tif attachment to the collection the following exception is thrown sporadically:

TISAppenderLog4net.LogConfiguration+Log4NetException: Failed to write 110\226\358493d1-b21b-49f7-851f-195ecff0a64e\KE150202024455452-478fe0f7-c226-467b-afd1-ce4d00388d71.tif file with length 4653, to path  ---> System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: Failed to write 110\226\358493d1-b21b-49f7-851f-195ecff0a64e\KE150202024455452-478fe0f7-c226-467b-afd1-ce4d00388d71.tif file with length 4653, to path 

I tried to reproduce the problem on our test environment, but I couldn’t. Everything was fine. Has anyone of you seen the exception before? 



## **Answer / Solution** ##

I see that the issue is well known and has to do with the length of the path.












