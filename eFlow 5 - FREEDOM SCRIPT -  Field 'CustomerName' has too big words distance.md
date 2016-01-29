# **eFlow 5 - FREEDOM SCRIPT -  Field 'CustomerName' has too big words distance** #

## **Question / Description** ##

  During the test of a field in Fanalyzer (eflow 5.0.3.6 SP1) I am getting the following message:

    Field 'CustomerName' has too big words distance

![](http://i.imgur.com/N5CfjPs.png)

I have checked the space between the words is around 23 pixels. Only one of them is 25 pixels. The image is 240 dpi so it is a normal space between words. I am afraid  this is defined for instance to be maximum 25 pixels, this value would be ok to 200 dpi images not to 240 or 300.

Some of you know a way to define this threshold?  What is the maximum distance between words in a Sentence field?



## **Answer / Solution** ##

An update:

I have found why Freedom is complaining about the space between words

![](http://i.imgur.com/GrmNutp.png)

It is because the FULLPAGE result.  I have seen in the LINES list that I have

One line with  JOSEFA DE MORAIS SOUSA
And another line with the words ALVES  (2nd word in the image above).

Because this, the space between the words  JOSEFA and  DE is too high

I need to find a way to improve the FULLPAGE result and avoid this error.
