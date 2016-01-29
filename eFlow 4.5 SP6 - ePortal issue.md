## eFlow 4.5 SP6 - ePortal issue  ##

### Question/ description: ###
I am trying to prepare a demo including ePortal for SSA in the US.

For connectivity issues I am trying to use either MSG or file import:

- For MSG I get an error about missing assembly Tis.Import.ePortal.Connector.MSG.dll (see log below)
- For file import it creates collections but gives the errors attached and continues to import the same image over and over again

Any ideas are welcome (I have installed ePortal + dependencies).

Also attached my log file.

Log for MSG:

`System.IO.FileNotFoundException: could not load file or assembly 'Tis.Import.ePortal.Connector.MSG' or one of its dependencies. The system cannot find the file specified
.......` 

### Answer: ###

Thanks for the suggestions:

- The winner for FileImport is Guillermo Grillo
- The solution from Guillermo to avoid reimporting the same file: `set DeleteOnRemote = true` works fine
- The config file I attached indeed only enabled MSG, but I already tested file import , and changed before sending the file.