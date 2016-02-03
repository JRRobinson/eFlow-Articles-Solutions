# **eFlow 5 - Validate station display the yellow highlight in wrong position** #

## **Question / Description** ##

I am preparing a demo and I need to use the Validate station to show the data captured by Freedom, (eFLOW5 5.0.2.2) but as you can see in the screenshot attached, although the data was well captured the ImageViewer is showing the yellow highlight in a wrong position.

I already tried changing the level of zoom, but does not fix the issue.

Is this a bug or can I set something in the Validate station to fix this problem?.  

![](http://i.imgur.com/ZepEcjd.jpg)



## **Answer / Solution** ##

The problem arises when the Validate station use the PRV instead TIF.  If you configure the station to download just the TIF, the highlight is located in the right place. 
















