# **eFlow 5 - AppFabric setup crash over Windows 2012 Standard** #

## **Question / Description** ##

I am installing a VM with Windows Server 2012 Standard (all patches installed), but when I try to install the AppFabric Server 1.1 x64, I am getting the following error message.  Of fact I have no chance to load the installing GUI, I do the double clicm over the executable and the error is generated immediately

I tried a lot of different workarounds found googling but with no success.

Any clue?

![](http://i.imgur.com/oz6Mq4Z.png)

Below is the full detail:

Description:
  Stopped working

Problem signature:
  Problem Event Name:                        CLR20r3
  Problem Signature 01:                       setup.exe
  Problem Signature 02:                       1.0.0.0
  Problem Signature 03:                       4ed52225
  Problem Signature 04:                       Setup
  Problem Signature 05:                       1.0.0.0
  Problem Signature 06:                       4ed52225
  Problem Signature 07:                       1fb
  Problem Signature 08:                       6
  Problem Signature 09:                       System.InvalidCastException
  OS Version:                                          6.2.9200.2.0.0.272.79
  Locale ID:                                             1033

Read our privacy statement online:
  http://go.microsoft.com/fwlink/?linkid=190175

If the online privacy statement is not available, please read our privacy statement offline:
  C:\Windows\system32\en-US\erofflps.txt


       

## **Answer / Solution** ##

The issue arose because the SETWOW was in ON state. Running LDR64.EXE SET64 fixed the problem.




