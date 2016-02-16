# **eFlow 5 - Calling an .exe via code autoruns simpleauto Station** #

## **Question / Description** ##

I have an EPortal application where I want to Start a Process via code to extract from a pdf an xmlfile.

Starting the station manually everything is fine. But If I start autorun I got the Error “the system cannot find the file specified”

Here the code I used now 

![](http://i.imgur.com/d3xWUdF.jpg)


## **Answer / Solution** ##

 I just get path form the registry and can call now the .exe also from autorun modus

try

{
    using (RegistryKey key = Registry.LocalMachine.OpenSubKey("Software\\Wow6432Node\\TopImageSystems\\eFlow 5"))
    {
        if (key != null)
        {
            Object o = key.GetValue("eFlowPath");
            if (o != null)
            {
                String path = o.ToString();
                //do what you like with path
            }
        }
    }
}
catch (Exception ex)  //just for demonstration...it's always best to handle specific exceptions
{
    //react appropriately
}

Even though it might not be relevant the context of your problem because you might only have a single ePortal, the code below is problematic in case you are using it like that (I just mention this because you do will not notice the problem if you are just working and testing on a single machine).

Maybe it has changed in recent Windows versions (I am pretty sure not in Windows 7), but the below code will only work if eFlow (32 bit) is installed on a 64 bit OS and that is exactly what the term “Wow6432Node” indicates. That means if you are installing eFlow on a 32 bit OS, the below code will not work because the returned registry code will be null. The registry queries are not behaving the same way “Program Files” does where this mapping is done automatically (I mean vs. “Program Files (x86)”).

To overcome this I am querying both registry keys (including “Wow6432Node” and without it) and check if they exist. There might be a better way, and it might not even be necessary anymore in new Windows versions, not sure about it.
