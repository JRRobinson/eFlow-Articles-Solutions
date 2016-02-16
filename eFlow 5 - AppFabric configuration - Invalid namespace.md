## eFlow 5 - AppFabric configuration - Invalid namespace ##

### Question/ description: ###
I get a amachine with some issue; when I try to configure appfabric, I get invalid namespace error.
Appfabric is installed but its services are disabled, eFlow works correctly with AppFabric disabled.

So far I narrowed it to this (powershell):

Done from Done from BAD MACHINE

gwmi -namespace root -class "_Namespace" | select Name

Name

--

DEFAULT

SECURITY

ccm

WMI

Done from Done form GOOD MACHINE

gwmi -namespace root -class "__Namespace" | select Name
 
Name

--

subscription

DEFAULT

cimv2

Cli

Nap

SECURITY

SmsDm

CCMVDI

RSOP

ccm

WMI

directory

policy

Interop

Hardware

ServiceModel

Microsoft

aspnet

*Lots * of classes are missing in the bad machine.

Any suggestions why this happened and how this should be fixed? Reinstall .NET?
 
### Answer: ###

I rebuilt the wmi repository whit the script below; appfabric can be configured

[http://http://blogs.technet.com/b/askperf/archive/2009/04/13/wmi-rebuilding-the-wmi-repository.aspx](http://http://blogs.technet.com/b/askperf/archive/2009/04/13/wmi-rebuilding-the-wmi-repository.aspx)

    sc config winmgmt start=disabled
    net stop winmgmt /y
    %systemdrive%
    cd %windir%\system32\wbem
    for /f %%s in ('dir /b *.dll') do regsvr32 /s %%s
    wmiprvse /regserver

    ::winmgmt /regserver --NOT SUPPORTED IN WIN 2008 -- use regsvr32 wmisvc.dll instead
    regsvr32 wmisvc.dll
    
    sc config winmgmt start=auto
    net start winmgmt
    for /f %%s in ('dir /s /b *.mof *.mfl') do mofcomp %%s

It's much better now:

gwmi -namespace root -class "__Namespace" | select Name
 
Name

--

subscription

DEFAULT

cimv2

Cli

Nap

SECURITY

RSOP

ccm

WMI

directory

policy

Interop

Hardware

ServiceModel

Microsoft

aspnet

Namespaces still missing compared to that other machine:

CCMVDI

SmsDm