# **Compiling Source Code** #

## **Question / Description** ##

Our customer StatLa Nord has problems with compiling source code. He gets the following message:
 
Since last Windows7 update VisualStudio2010 throws a large number of errors. After relinking two custom and one standard DLLs the errors don't occur any longer. But the following warning remains: Warnung 1 Der Primärverweis "Completion.ApplicationServices, Version=4.5.1.0, Culture=neutral, PublicKeyToken=0752346849557bc9, processorArchitecture=MSIL" konnte nicht aufgelöst werden, da er eine indirekte Abhängigkeit von der Frameworkassembly "System.Web.Extensions, Version=1.0.61025.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" aufweist, die im derzeit als Ziel angegebenen Framework nicht aufgelöst werden konnte. ".NETFramework,Version=v2.0". Zur Beseitigung des Problems muss entweder der Verweis "Completion.ApplicationServices, Version=4.5.1.0, Culture=neutral, PublicKeyToken=0752346849557bc9, processorArchitecture=MSIL" entfernt oder die Anwendung erneut als Ziel für eine Frameworkversion verwendet werden, die "System.Web.Extensions, Version=1.0.61025.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" enthält. StatLa.Verbund.Global
 
Does anyone know what to do here?



## **Answer / Solution** ##

Using Framework 3.5 did the trick. 










