## eFlow 5 - csm.Application.Configuration.GetSection(Section).GetParam(Subsection,Param) ##

### Question/ description: ###
What is the equivalent of (please see below) in eFlow 5:

csm.Application.Configuration.GetSection(Section).GetParam(Subsection,Param);

The "Configuration" object/ namespace has been removed from the API and it is no longer available.

### Answer: ###
Figured it out after some deep investigation...

    using TiS.Core.TisCommon.Configuration;
    ...
    var r = ((ConfigData)csm.Application).MachineConfig.GetSection(Section).GetParam(Subsection, Param); 