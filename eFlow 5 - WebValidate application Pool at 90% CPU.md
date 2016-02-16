# **eFlow 5 - WebValidate application Pool at 90% CPU** #

## **Question / Description** ##

A customer is requesting to justify why they discovered in a Quality environment that the system was unusable due to a peak in the CPU, related to App Pool of the WebValidate (Web Completion) at 90%.

In the target environment maximum a bunch of people where connected simultaneously (very likely 2 to 4 people) to WebValidate.

In this scenario I am not able to provide any good reason, if not by considering a bug like resources locked or not released for some reason.

No idea at all, and not good as well with such a poor volume so any good idea is really appreciated.


## **Answer / Solution** ##

I am not going to tell why that happened but I believe that it could be good for you to know that by using the specific setting, visible in the red rectangle of the attached image, you can recycle the app pool at a certain time on the server. This means that it is possible to schedule it for renewing on a daily base, for us when the people in completion are not working.

In order to do it, follow the steps here : https://technet.microsoft.com/en-us/library/cc754494(v=ws.10).aspx
As visible there are even more options for keep it under control.

For sure this is more efficient.

![](http://i.imgur.com/SiVPyOS.png)