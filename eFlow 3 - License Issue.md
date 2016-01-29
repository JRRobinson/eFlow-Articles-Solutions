# **eFlow 3 - License Issue ** #

## **Question / Description** ##

Error: Disk RTI subsystem is Damaged

Receiving the above error message on the Priviledge Licensing System.


## **Answer / Solution** ##

There are 2 answers to this issue.

Short fix version:
 
For fixing the error you need to do the following:
 
1. Open c:\boot.ini
2. Write /noexecute = AlwaysOff
3. Reboot the system.
4. Go to c:\ProgramFiles\Aladdin\Privilege and run InstallPrivilege.exe.
 
Longer version:
 
If this is the case so I suggest following solution steps below:
 
Sometimes eFLOW3 installation on a windows server may require a special installation procedure for privilege 3rd party licenser.
 
Please follow the solution steps below for the installation of Privilege:
 
When running the default eFlow installation on a windows, the Aladdin Privilege Administrator returns an error or is not installed at all.
Examples of errors: 

1. Blue screen.
2. Data encryption/decryption failed.
3. Unknown error
1. Blue screen displayed when running .NET applications Enveloped with IMAGE_EMULATION enabled.
2. Encryption/decryption failed with McAfee Anti-Virus installed.
3. Data protection error - "Unknown error"
 
Solution steps:
Before installing eFLOW3
1. Open the c:\boot.ini file
2. Add the following option /noexecute=AlwaysOff to machine parameter line. See attached boot.ini sample.
3. Reboot the machine.
4. Install eFLOW normally.

Note: if eFLOW already installed, you can still follow steps 1-3 above to fix the problem without uninstalling eFLOW, then install Privilege component manually by running the following installation program:
c:\Program Files\Aladdin\Privilege\InstallPrivilege.exe.

AFTER eflow installation (only for versions prior to eFLOW 3.1 build 3.170)
1. Unzip the attach file (hinstall.zip)
2. Run Hinstall.exe






















