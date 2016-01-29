## eFlow 4.5 - SwitchToJpg Button ##

### Question/ description: ###

It is possible to reach the Completion functionality of SwitchToJpg button via code?


### Answer: ###
    TiS.DataEntry.IStationAcccess station=Tis.DataEntry.StationCreator.Singletoninstance;
    station.Configuration.GeneralSettings.Behaviour.AllowSwitchToJpeg