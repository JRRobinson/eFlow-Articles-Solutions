# **eFlow 4.5 - Collection Organizer error to put collection ** #

## **Question / Description** ##

I am not succeeding to put a collection from Collection Organizer station, it was shows an error in LOG complaining about fail to save the TIF file. No message is presented to the user, and the collection remains in the queue. Any suggestion will be welcome.

See errors below please

Failed to upload attachment [C:\TIS\eFlow 4.5\AppData\Client\EflowExams\WorkDir\E40CM0017_E40FP00010.TIF]. Details : [The process cannot access the file 'C:\TIS\eFlow 4.5\AppData\TIS-BRAZIL-01\EflowExams\Dynamic\41\180\67728be2-68e7-459c-aced-deef48c4b2a2\0000000005_E40CM0017_E40FP00010.TIF' because it is being used by another process.]



## **Answer / Solution** ##

This happens when this was previously accessed and it was not properly closed.

I would suggest in the custom code before you retrieve the file to add a call to the function that does the file open twice (wrapped around a using clause and inside a try catch) this should force the file to become unlocked, thus available to be read again.

There is no custom code in place, pure collection organizer station.

You can see it is the core file in the server dynamic where no client touches it,  so it is a core issue.

Then the CO station is finalising properly the close file operation.  I would raised thie with R&D, not good.

A possible workaround is to write some custom code that looks specifically for files under this folder and opens and closes them, so that when the CO tries to open them again, the files handles are all closed and it will not fail to open the file in question.

In short, bad coding on the CO station when accessing the file because it leaves the file handle opened and it should not.

We never handle files in the Server dynamic folder, collection organizer shouldnt do this too, so looks like a core issue, will try to reproduce in simpledemo and open a case.





















