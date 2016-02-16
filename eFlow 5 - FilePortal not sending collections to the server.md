## eFlow 5 - FilePortal not sending collections to the server ##

### Question/ description: ###
After changes to the CAB (renaming field and layouts) FilePortal stopped sending collections to the server. 

Clearing Temp, reinstalling CAB, resetting IIS doesn't help...

eFlow 5.0.3 (no SP)

### Answer: ###
Issues found:

- Metatags out of sync - solution reinstall the CAB (export, delete and import)
- Metatags source empty (thanks to Ben and Stefan for pointing out) - add sources and reinstall the cab (export, delete and import)
- SLAs out of sync - go to supervise, remove existing SLAs and reinstall the CAB (export, delete and import without SLAs assignment)
