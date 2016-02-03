# **eFlow 5 - PRD File not found by Freedom activity** #

## **Question / Description** ##

I managed to import PDF searchable in my application by using ePortal+PDFTools. As you can see the dynamic folder on the server contains, among other things, my 15KB PRD File.

![](http://i.imgur.com/HQWK9zU.png)

I built a very simple recognition flow with just a freedom activity, as no PageOCR should be necessary. I made sure that my Recognition station receives PRD in the attachment files list:

![](http://i.imgur.com/Asg4R8r.png)

Probably not necessary, but I flagged DRD and PRD also in the Attachment Type->Save tab of my mailPortal station.

Even so, my Reco station complains about the PRD being missing:

![](http://i.imgur.com/HOeaPRw.png)

Looking inside the Client/Workdir folder at runtime, the station actually loads only the TIF and the PDF files from the server, not the PRD.
Any help or comment is appreciated.




## **Answer / Solution** ##

CleanCollection checkbox can be a reason for this behavior.

![](http://i.imgur.com/sLbvbId.png)







