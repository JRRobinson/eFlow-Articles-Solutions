# **eFlow Disaster recovery ** #

## **Question / Description** ##

A client wants to setup disaster recovery for their eFLOW servers. The client is considering backing up the server data every hour? 

I’m looking for some recommendations as to common practices, softwares to be used? 

 

## **Answer / Solution** ##

My recommendation is usually:

- Make sure you can rebuild the machines quickly (i.e. have images, snapshots if you use vms or automated deployments -- yes, 4.5 can be installed silently for example)


Seriously: I consider eFlow an interim system, usually. Most of the collections should just move right through the workflow. Unless your project is totally different I'd say: Convince the client that they should have a backup of the input files, should be able to recreate the eFlow machines (biggest issue will be: How do you get a production license in an hour) and .. forget about the rest.

Worst case scenario: The collections in your flow are gone. Recreate them from the input backup, eat the additional typing effort if necessary. Back of the envelope calculation: How many collections do you have in your system at any point in time? How many of those contain information that was user-generated (i.e. not just a collection that sits in a queue, a collection that contains completion information)?

I'd say the number is too low to warrant a big backup plan.

Issues with the statement above:

- If you use a scanportal, everything changes (getting out a specific piece of paper sucks. Finding a TIF to import again should be trivial)

- I assume that the company has a way to create a diff (What part of the workload of today and yesterday was already correctly processed) that is reasonably cheap and easy.
























