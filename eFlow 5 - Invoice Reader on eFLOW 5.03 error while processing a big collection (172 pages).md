# **eFlow 5 - Invoice Reader on eFLOW 5.03/error while processing a big collection (172 pages)** #

## **Question / Description** ##

A collection of 172 pages is being processed in recognition station, at the end it comes up with the error message below and then goes to the reject station. (Message is from the message window of the recognition station)
 
As far as I watched out the TIF File, those Chinese characters at the end of the error message are not part of it.
 
Does eFLOW itself or some engine use Unicode surrogate characters (as indicated in the error message)? 

![](http://i.imgur.com/eq696HS.jpg)

## **Answer / Solution** ##

This was a bug in previous versions, solved with eFlow 5.1. 

