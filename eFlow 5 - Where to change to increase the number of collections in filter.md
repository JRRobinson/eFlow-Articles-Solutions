# **eFlow 5 - Where to change to increase the number of collections in filter** #

## **Question / Description** ##

I am looking for a way to increase the current “Collections presented in a queue” limit of controller (Eflow 5.1 SP1) .   1000 for high volume projects it is too low.


## **Answer / Solution** ##

I had a few minutes to connect to my customer server. At this time I have changed the file in
C:\Users\myusername\AppData\Local\TIS\Controller\Application\   (Appdata is hidden by default)  as you suggested

And it worked!!!   But controller becomes really slow, it seems.  ( I have changed to 10000).  Why multiple places to store the same file is the big question.

We have this appconfig.xml in

Programdata\tis\eflow 5\Server\appname\setup
Programdata\tis\eflow 5\Client\appname\Workdir
C:\Users\myusername\AppData\Local\TIS\Controller\Application\   

Only changing the last one did the trick.
