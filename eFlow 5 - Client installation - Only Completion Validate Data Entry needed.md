# **eFlow 5 - Client installation - Only Completion/Validate/Data Entry needed** #

## **Question / Description** ##

I want to only install Completion on a client PC. What is the best way?

![](http://i.imgur.com/vrk2wmA.png)


Is it simply a matter of removing the components in the list above?



       

## **Answer / Solution** ##

Don't just install client user station module, You must install recognition module else manual patch several files and register them from the installer files.  There is a bug in current installer, if you forgot then your completion shows no image at the image viewer, same with controller view collection.

In my case, when I only include Recognition and Manual Stations, Completion is still not working for me. I needs another dll, Application(s)Common(s).dll (sp?) for it to work.




