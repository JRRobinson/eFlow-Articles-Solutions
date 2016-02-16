## eFlow 5 -Autorun not starting up ##

### Question/ description: ###
We have eFlow 5.1.0.14 working except for autorun stations.

Service for autorun is running on local (and domain) administrator but we are getting following errors.

    FATAL Source App: eFlowAutorunStationStarter.exe, Message:
    ....
    The cummunication object cannot be used for communication because it is in faulted state.
    
    FATAL Source App: eFlowAutorunStationStarter.exe, Message: 
    Login fail for user: "AKQUINET\Adam" - Windows Authentication is not allowed.

### Answer: ###
Eventually we fount out that in to TisConfiguration.config files (in eFlow 5 and TisDefaultSTS folders) we had different entries, one had 'windows 'word, which is correct and another one had "win " only, which is not enough.

Correcting this made things working.