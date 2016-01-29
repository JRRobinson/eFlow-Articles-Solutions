# **eFlow 5.0.3.6 Design Error** #

## **Question / Description** ##

A customer had been working on creating fields in Visual Designer for one week.  VD then crashed, now everytime they open Design they get this error.

![](http://i.imgur.com/r4YLGaH.png)

The above error is followed by a few Address Violation exceptions.

Iisreset does not help (because this seems to be a data related error). Export and re-import CAB does not work.

Now they run the risk of losing one week of work. How can I recover the application? Any tip?



## **Answer / Solution** ##

Using CSM to delete a relevant problematic field helped restore it. At least they only need to re-create the field and not the whole thing.



----------
In response to Guillermo’s question, and I believe it might be useful for others as well, what’s causing the integrity problem with the flowset is:

-	There are 2 records of the intended same field in the flowset.xml but in different case, i.e. fieldABC and fieldabc. This is likely due to the customer attempting to correct the case of the field name, e.g. from fieldabc to fieldABC.
-	In CSM, only one instance of the field is listed. Once I removed this field, it’s working fine.

I have also encountered Visual Designer’s inconsistencies with field name cases a couple of times before. 

So related moral of the story? Do not #YOLOSWAG change the field name case by simply renaming the field in VD. VD is not well notified of the case change in the field name and does not handle it very well. You’ll want to at least delete the field, save, and possibly restart application (to make sure the previous record is cleaned) before re-creating it.
