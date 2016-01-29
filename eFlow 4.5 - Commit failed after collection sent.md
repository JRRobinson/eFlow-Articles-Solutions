## eFlow 4.5 - Commit failed after collection sent  ##

### Question/ description: ###
eFlow 4.5.1.700 SP4

During import of images , using custom code in SimpleAuto, there is a query to verify that a collection has been sent to workflow after FreeCollection has been called and then original image file is deleted from disc.

If the query does not find the collection (using collection name), the image file is not deleted.
In addition, when all is OK, a record is inserted in another DB table with NEW status (update when fully processed).

It seems like even though it appears as if the collection was sent, it might still not be processed in eFlow, ans Commit fails errors appears.
Since the image was never processed completely, and does nit appear anywhere else n the workflow it seems like the previous sentence might be true.

HAS ANYONE SEEN THIS SITUATION? 


### Answer: ###

In my opinion the key is to determine what is causing the COMMIT to fail.


The most likely option is that the Windows user logged on the machine on where the FilePortal runs has restricted rights to the _workflow DB. This is a likely scenario fro the COMMIT to fail.

