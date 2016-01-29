# **E_Session Ghost entries on latest eFlow 5 (5.0.3) - also kills Controller** #

## **Question / Description** ##

When this station ran, the eFlow process responsible for clearing the entries on the E_Session _workflow database table (either the Auto run service, the TIS AppPool IIS service or the station itself - not sure which of these is handling this bit), left behind the entries on the E_Session table as if the "Recognize" station was still running. 

There's no pattern to reproduce this, because I checked other tables that should be updated when the station runs and the entries were not present there, so it was only on E_Session where these entries were left behind.

So in short, in some occasions, when some stations run, the process responsible for "clearing up" the station running instances info on the _workflow DB might not cleanup the corresponding entries (row / records) on the E_session _workflow DB, thus leaving the feeling that the station is still running and this also triggers on error on the station itself (when clicking on the station icon on the Controller - "Invalid Node Name []"), which actually causes the Controller to crash and literally kills the process.


## **Answer / Solution** ##

Forgot to mention that the problem was resolved by running a DELETE SQL statement on that E_Session table and targeting the station ID that corresponds to the affected station.

This is the workaround. 



















