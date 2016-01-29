# **eFlow 5 - A problem was found in the latest OCRs version** #

## **Question / Description** ##

This is to inform you about an issue we found in the latest OCRs installation (5.1.0 SP1). 

Symptom:

•	After uninstalling the previous OCRs version and installing eFLOW 5.1.0 SP1 version of OCRs, Oce engine is not working. 

Reason:

•	Under the ODT-OCE registry key HomePath  value is not written correctly : ‘C:\Program Files (x86)\TIS\eFlow 5\OCRsOce’.

  

        

## **Answer / Solution** ##

•	You need to add the missing slash between OCRs and Oce(see below) 

![](http://i.imgur.com/u8CJ5ny.jpg)



