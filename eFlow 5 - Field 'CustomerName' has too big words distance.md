## eFlow 5 - Field 'CustomerName' has too big words distance ##

### Question/ description: ###
During the test of a field in Freedom analyser (eFlow 5.0.3.6 SP1) I am getting the following message: 

    Field 'CustomerName' has too big words distance

I have checked the space between the words is around 23 pixels. Only one of them is 25 pixels. The image is 240 dpi so it is a normal space between words. I am afraid this is defined for instance to be maximum 25 pixels, this value would be OK to 200 dpi images not to 240 or 300.

Some of you know a way to define this threshold? What is the maximum distance between words in a Sentence field?

I'm not using IR or FDDBs. 

### Answer: ###
I have found why Freedom is complaining about space between words. It is because the FULLPAGE result. I have seen in the LINES list that I have.

In the Image we have a name : JOSEFA ALVES DE MORAIS SOUSA

But in the PRD I have this name split in 2 lines (not in the same line)

One line with JOSEFA DE MORAIS SOUSA

And another line with the words ALVES (2nd word)

Because this, the space between the words JOSEFA and DE is too high.

I need to find a way to improve the FULLPAGE result and avoid this error