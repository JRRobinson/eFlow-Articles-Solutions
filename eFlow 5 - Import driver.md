# **eFlow 5 - Import driver** #

## **Question / Description** ##

May I know how to get Import driver setting at Scan Portal?  I am using Win 7 – eFlow 5.0.0.2.   Any help much appreciated.

## **Answer / Solution** ##

I just figured around with it last week as I do have to do a Scan related presentation using eFLOW 5 this week and don’t have a scanner…
 
After searching the web for free TWAIN file Importers I finally I ended up searching an old 4.5 Machine for the Keyword IMPORTER (got it somewhere from 4.5 TISconfig scanner settings)  and came across the content in the folder E:\Windows\PixTran. So I replaced the eFLOW 5.x machines folder E:\Windows\PixTran  folder with the content the Machine having eFLOW 4.5 SP4 installation as a very last try. And … I was surprised that it did the trick

[http://https://app.box.com/s/if5d38vatwipzisb2y1j](http://https://app.box.com/s/if5d38vatwipzisb2y1j) 

Thanks for your solution. I tested the import driver. it can scan the image but Is it only support 300 DPI? How can I change the resolution to 200 DPI. 

![](http://i.imgur.com/OfmiNaB.png)

It can be changed from the configuration file manually.

Go to your Configuration folder and find the xml file, go to Import Driver section, and change the Xresolution and Yresolution to 200.

![](http://i.imgur.com/37kRp7u.png)



