## eFlow 5 - Freedom question ##

### Question/ description: ###
I'm trying to work out an approach to recognize the social number from various documents.

I want to capture the SSN number from about 100 different types of documents, each with up to 5 different variations. In all of the documents, the keywords are easily available and the number is always in the top right hand corner, please see link below 

[http://app.box.com/s/vqveoup65uqo53tvbsye](http://app.box.com/s/vqveoup65uqo53tvbsye)

### Answer: ###
You should be able to remove the lines at OCR Engine level (field), provided this strategy does not impact the recognition result that much.

From my experience, the line removal at the engine level usually does not work as well as FormOut, in that it impacts the results much more due to part of the live text being removed. In my case, the hand-writing is not neat at all so a lot of times, the numbers do touch or go over the box lines.