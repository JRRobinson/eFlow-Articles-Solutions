# **eFlow 5 - How the recognition station work with multi-cores** #

## **Question / Description** ##

My customer ask me a question how the recognition station work with multi-cores. I paste his question here. Anyone know the answer?

We have two VMs running Recognition. One is the main server. It has 2 CPUs and 16G RAM. The other one has 2 CPUs and 8G RAM which is dedicated for Recognition. RAM usage is not that high. Normally under 4G. The intention is to move the Recognition off the main server to the 2nd VM. Or move to a 3rd VM which we are a bit hesitating as it costs more. I think my question is if we add 2 more CPUs onto the 2nd VM, would it have the same effects as if we create a 3rd VM? 

I am not sure how the Recognition utilises the CPUs. Is it running across all CPUs or just allocate one CPU to run a single instance? E.g. If we had 2 Recognitions on a 4 CPUs VM, would it be assigned all 4 CPUs or only 2 CPUs? In the former case, we probably would end up 100% CPU issue again. Can you please advise?






## **Answer / Solution** ##

There is eFLOW 5 performance test report.  You could see the performance, the infra and number of VMs used to deduce.  It could be tough.  Below is another alternative based on my knowledge and experience.  Hope that they help.
 
 
Based on my testing and understanding, each instance of recognition can use 1 CPU if it is available.  You can verify this easily using Simple Demo.  Look at the screen shot and you could see efProcessShell.exe (3 of them, 3 instances), the CPU 0, CPU 1 and CPU 2 were having the “graphs” accordingly…..
 
If you have less CPUs than your number of instances then the CPU time were shared among the instances and run slower.  You can test it using dual core machine and look at the resource monitor (I think windows 8 onwards and 2008 R2 onwards should have this tool).
 
Please see my comments (to the best of what I knew) below to the questions you have raised.  Hope that these help.

![](http://i.imgur.com/WQ3j0BO.jpg) 








