# **eFlow 5 - Autorun stations running ghost** #

## **Question / Description** ##

I have a problem with Station that are running and I cannot locate them and close them.
        
1.       In the Controller you can see 3 station running.

![](http://i.imgur.com/E6fbK4w.jpg)

2.       Nothing is visible in the in Station.
3.       Nothing is visible in the Processes in Windows Task Manager.
 
Any suggestions? How to close them? What to look for?


## **Answer / Solution** ##

In eFLow 4.5 you had a permanent connection (remoting) to eFlow. That _was_ for all intents and purposes your session. Kill a process, connection gone, session gone.

eFlow 5 is different. Servers are supposed to be stateless. Clients just say 'Give me a collection' and the server forgets about that client again. There are still ~Sessions~, in the DB. Because the server needs to lock the collection _for a given user_. Since there's no open/persistent connection though, the server cannot terminate sessions in a timely manner. They just expire if they aren't used.

In other words: 'Ghost' sessions are to be expected. If a client shuts down cleanly/in a nice way it _can_ say 'Btw, I'm calling it a day'. But if they don't, the server-side session is going to stick around until eFlow decides that this client is gone.




