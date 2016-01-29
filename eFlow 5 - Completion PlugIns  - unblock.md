# **eFlow 5 - Completion PlugIns  - unblock** #

## **Question / Description** ##

We got always problems after installation with Completion PlugIns (5.0.2.2, Server 2008 SP2 64bit). Aurelien told me, it is necessary to “UnBlock” such assemblies after copy from another source. Other event assemblies don't make any trouble.

![](http://i.imgur.com/mLVgPeI.png)

![](http://i.imgur.com/ZjothDS.png)




## **Answer / Solution** ##

The UI in the screenshot is showing a default Windows feature - Explorer stores information about the source of binary files in an alternate stream (so as far as I know, this works only if you're using NTFS. If you're not, please for the love of god kill that Windows machine now).

If you download your completion plugins from a random host AND that host isn't trusted, then you'll end up in this situation. There's probably a way to prevent that behavior globally, but that's about as bad as turning off UAC 'just because'.

