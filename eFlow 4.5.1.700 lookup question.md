# **eFlow 4.5.1.700 lookup question** #

## **Question / Description** ##

Do anyone know the below “Page size” in lookup SQL setting.

What is the maximum value?

I using eFlow 4.5.1.700

![](http://i.imgur.com/9pKWOef.jpg)  

        

## **Answer / Solution** ##

Only info found that I could find relevant, see below.  Not sure page size = 1000 is equivalent to how many records.

![](http://i.imgur.com/4SWONlQ.png)


----------
I tested it – this is the actual number of records that will be presented to the user while filtering during typing. Take a look at the attached print screens. In this case, page size = 5

![](http://i.imgur.com/LOedfIb.jpg)

![](http://i.imgur.com/pa4uP1R.jpg)


----------
So the dropdown list shows 10 records where it duplicates the 5 unique records when you have page size = 5.  When you have page size = 2 then 5 sets of duplicates.  Strangely why the list must show 10 records and those that exceed the page size will become repeated set (duplicates).  It is a bug.

As you said, normally others used default page size = 1000 and usually returned records do not exceed 1000 records then no duplicates will appear.


