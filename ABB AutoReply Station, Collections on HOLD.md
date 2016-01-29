# **ABB AutoReply Station, Collections on HOLD** #

## **Question / Description** ##

Please see the screenshot, for both collections I set the error code 0008 in Exception, now they are hanging in AutoReply on Status HOLD because of „Object reference not set to an instance of an object.“

![](http://i.imgur.com/sflY9fY.png)


## **Answer / Solution** ##

It seems purely a configuration issue – the AutoReply runs on the W05 machine which is not explicitly mapped in ePortal configuration.

Please let me know if/when I can fix this.

The action: stop Autorun, add the entry in ePortal.xml, start Aurotun.

![](http://i.imgur.com/IF6t0s4.png)



