# **eFLOW 4.5 - Missing WFU.dat ** #

## **Question / Description** ##

We are using in a Project 4.5.2.174 (SP5). Today we had some disconnections from the server (don’t know the reason yet), and one of the collections that was in the workflow  for the last 3 days, have went to Reject queue. When I try to view the images from the Controller, I  can see the message in the logger  complaining about missing WFU.DAT. I have check in the dynamic directory and it is not there. 
 
Is there some trick to create an fresh WFU.DAT ? I would like to don’t need to ask the customer to scan again the collection.  If I could create an initial WFU.DAT, I could put in the dynamic and move the collection back to the begin of the workflow.
 
Please let me know if there is some trick to this.



## **Answer / Solution** ##

The WFU.dat _is_ the collection. It's (more or less) the serialized TisCollectionData, as the workflow stores it. WorkFlowUnit => WFU.

There's no excuse for losing that file, but to proceed with your collections: Why don't you reimport the images using the FilePortal?




























