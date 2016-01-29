# **eFlow 4.5 - Controller indicators 4.5 SP6** #

## **Question / Description** ##

I am looking at the controller color indicator below the stations and I know that we can change the parameters.

Appreciate if someone who have experience configuring the controller parameters can give me a “run through” about the indicators, what do they represent and how parameter modifications should affect the colors.



## **Answer / Solution** ##

This doesn't work as far as I know.

I had to "hack" this once (inject some code)



Following our conversation, I've made a fix for this issue happening on the Controller on build 595 (I can also make it in a couple of minutes on build 4.5.2.63 if you send me the BIN later). This fix is "incorporated" (embedded) into the Controller. 
 
The fix is available here: ftp://ftp.tis.co.il/20120618_eFlow595Bin/efControl.exe
 
(also available here: [https://www.box.com/s/2ffb8c47144518ca2ab8](https://www.box.com/s/2ffb8c47144518ca2ab8))
 
 
First let me explain how the little progress bar turns red (or not) for any given station. 
 
 
What determines the coloring of the bars underneath any given station:
 
 
Basically if the "percentage" is equal or higher than 200%, the bar turns red. 
 
If the "percentage" is in between 101 and 199%, then little bar under any given station will have both a "grayish" and red coloring. 
 
 
The "percentage" is determined by this:
 
 
int nPercent = ( 100 * nForms )/nThreshold;
 
 
This is executed as follows:
 
 
private int GetWLPercentage( int nForms, int nThreshold )
{
int iResult = 0;
int nPercent = ( 100 * nForms )/nThreshold;
 
if (nPercent > 200)
{
nPercent = 200;
}
 
if (nPercent < 100)
iResult = (int)Decimal.Truncate( Decimal.Round( (nPercent/12.5m), 0)*12.5m + 0.01m );
else
iResult = (int)Decimal.Truncate( Decimal.Round( (nPercent/25), 0 )*25 + 0.01m );
 
return iResult;
}
 
 
Where: 
 
 
nForms - is the number of Forms on a given station.
 
nThreshold - Represents internally the WLThreshold (Workload Threshold) and is (unfortunately) a hard coded value of the Controller defined as:
 
public const int DEFAULT_STATION_WORKLOAD_THRESHOLD = 50;
 
 
When GetWLThreshold is called / invoked, the nThreshold value is multiplied by the number of instances running for a particular station, as follows:
 
 
GetWLPercentage(nFormsCount, nInstancesCount * nWLThreshold);
 
which actually is: nInstancesCount * DEFAULT_STATION_WORKLOAD_THRESHOLD
 
And because is hard coded, that's why changing any of the Threshold values through the Controller Options, has NO effect on the calculation of the "percentage", which determines if the little progress bar underneath any given station, turns red or not.
 
The "fix" basically allows the nThreshold to be changed (if desired) for any station, more than one station (or all of them) at will, in a very simple way, by adding / modifying the "WLThreshold" Registry Entry key under HKEY_LOCAL_MACHINE\SOFTWARE\TopImageSystems\eFLOW 4.5.
 
The WLThreshold key is a STRING value.
 
The value of the WLThreshold represents a JSON ([http://www.json.org/](http://www.json.org/)) array, which defines the nThreshold value for one or more stations.
 
Examples of possible WLThreshold values:
 
 
{"SimpleAuto":100,"Recognition":100}
 
{"Completion":80,"Recognition":1500}
 
{"Completion":80,"FreeMatch":200,"Export":1500}
 
 
Basically the number of stations that can be defined within the JSON array is limitless (only limited by the amount of characters allowed by a STRING type key value within the Registry).
 
Notice that the JSON array syntax always starts with a { and ends with }. Within the JSON array, the elements (for us the stations) are separated by a comma (,).
 
A station nThreshold value within the JSON array is defined by:
 
 
"Name_of_the_station_of_an_eFLOW_application":value_of_nThreshold_desireed_for_that_station
 
 
Notice that the "Name_of_the_station_of_an_eFLOW_application" should ALWAYS be enclosed in double quotes (as it is a JSON format requirement for a defining key element as a STRING).
 
Also notice that the value_of_nThreshold_desireed_for_that_station should NOT be enclosed in quotes, as in JSON it represents an INTEGER.
 
Within the same WLThreshold registry key, you can put any stations for any eFLOW application.
 
 
Also, the following notations are possible:
 
 
{"*":value}
 
{"all":value}
 
 
Examples:
 
{"*":80}
 
{"all":120}
 
 
Both "*" and "all" mean the same thing, which is to assign the value_of_nThreshold_desireed_for_that_station for ALL stations. 
 
It is important to keep in mind that Registry settings are local to each machine, so WLThreshold will be local to the machine where you define it and only applicable to the Controller instance running on that machine. So if you wish to have this fix working on other machines using the Controller, the WLThreshold registry entry should be created on that particular machine as well.
 
Needless is to say that the efControl.exe containing the "fix" should be deployed on each local eFLOW\Bin if you wish to have this functionality. 
 
If the WLThreshold is not defined within the Registry, the Controller will continue to use the default functionality, which is to use nThreshold as (DEFAULT_STATION_WORKLOAD_THRESHOLD = 50).
 
 
Just for Information:
 
Last but not least (has no functional implications for what was explained above), also the Controller option values (as seen through the Controller options Window, tabs: Queue Threshold & Session Thresholds) are now saved / loaded properly for each eFLOW application and are saved within the eFLOW\AppData\Configuration folder (of each eFLOW machine) under: 
 
<eFLOW_Application>.json file 
 
Example: SimpleDemo.json.
 
Contents:
 
{"0.MaxPPMAggregate":0, "8.SessionMaxPPM":0, "6.MaxFormsInQueue":0, "1.QueueMinPPM":1000, "2.SessionMinPPM":10, "4.SessionMaxPPM":0, "3.MaxFormsInQueue":2000, "4.MaxPPMAggregate":0, "7.MaxPPMAggregate":0, "5.WLThreshold":50, "2.SessionMaxSpeed":0, "9.SessionMinPPM":10, "1.Station":"efFreedomAnalyzer", "0.SessionMaxPPM":0, "0.Station":"Completion", "3.WLThreshold":50, "4.QueueMinPPM":1000, "9.SessionMinSpeed":10, "2.MaxPPMAggregate":0, "1.SessionMaxPPM":0, "0.SessionMinSpeed":10, "8.WLThreshold":50, "4.MaxFormsInQueue":2000, "1.SessionMinSpeed":10, "5.SessionMinSpeed":10, "7.QueueMinPPM":1000, "5.SessionMinPPM":10, "0.SessionMinPPM":10, "5.Station":"PENDING", "4.Station":"FilePortal", "3.QueueMinPPM":1000, "7.SessionMinSpeed":10, "8.SessionMinSpeed":10, "6.SessionMinPPM":10, "2.MaxFormsInQueue":2000, "8.MaxFormsInQueue":2000, "6.MaxPPMAggregate":0, "3.SessionMaxSpeed":0, "8.MaxPPMAggregate":0, "2.SessionMaxPPM":0, "9.WLThreshold":50, "3.SessionMinPPM":10, "8.QueueMinPPM":1000, "6.WLThreshold":50, "9.MaxFormsInQueue":2000, "4.WLThreshold":50, "7.SessionMaxPPM":0, "9.MaxPPMAggregate":0, "1.MaxFormsInQueue":2000, "6.SessionMinSpeed":10, "3.Station":"Export", "5.MaxFormsInQueue":2000, "2.Station":"Exceptions", "9.SessionMaxSpeed":0, "3.SessionMinSpeed":10, "4.SessionMaxSpeed":0, "0.SessionMaxSpeed":0, "4.SessionMinPPM":10, "7.WLThreshold":50, "5.SessionMaxSpeed":0, "7.MaxFormsInQueue":2000, "5.SessionMaxPPM":0, "6.QueueMinPPM":1000, "1.SessionMaxSpeed":0, "2.SessionMinSpeed":10, "0.WLThreshold":50, "5.MaxPPMAggregate":0, "3.MaxPPMAggregate":0, "5.QueueMinPPM":1000, "7.Station":"REJECT", "8.SessionMinPPM":10, "2.QueueMinPPM":1000, "6.Station":"Recognition", "2.WLThreshold":50, "0.MaxFormsInQueue":2000, "9.SessionMaxPPM":0, "4.SessionMinSpeed":10, "6.SessionMaxPPM":0, "8.SessionMaxSpeed":0, "1.SessionMinPPM":10, "7.SessionMinPPM":10, "1.WLThreshold":50, "3.SessionMaxPPM":0, "9.Station":"SimpleAuto", "7.SessionMaxSpeed":0, "9.QueueMinPPM":1000, "8.Station":"ScanPortal", "1.MaxPPMAggregate":0, "0.QueueMinPPM":1000, "6.SessionMaxSpeed":0}
 
 
Notice that the values are stored with the following notation as part of a JSON array:
 
"Number.Property":value
 
 
Examples:
 
"1.SessionMinPPM":10
"3.QueueMinPPM":1000
 
 
Where:
 
1.SessionMinPPM - represents the Session Min PPM property for the efFreedomAnalyzer station (index: 1 - second item showing on the list of the Session Thresholds tab of the Controller Options window).
 
3. QueueMinPPM  - represents the Min PPM property for the Export station (index: 3 - fourth item on the list on the Queue Thresholds tab of the Controller Options window).
 
 
These values were not being saved / loaded properly, and now as part of this fix, they are.
 
 
The "fix" is basically a JSON management class (available here: [https://www.box.com/s/ceaa9014346c126e52a8](https://www.box.com/s/ceaa9014346c126e52a8)) that was added through .NET run time reflection to the efControl.exe to make possible these functionality to work properly.










