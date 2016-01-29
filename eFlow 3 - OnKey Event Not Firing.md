# **eFlow 3 - OnKey Event Not Firing ** #

## **Question / Description** ##

We have a method hooked up to the OnKey Event in Visual Designer but this event doesnt fire when "TAB" is pressed it does if other keys are pressed, e.g. "A" ""B" etc

What I was hoping to do was to detect when the operator has "SHIFT + Tabbed" off a field (i.e. tabbing backwards)

Is this the expected behaviour?  in the eflow logger, I can see that it didnt try to fire the event


## **Answer / Solution** ##

Basically the problem is that the TAB key is not being fored on the OnKey event and the reason is that the TAB key stroke is reserved in eFlow 3 - as designed.






















