## eFlow 4.5 SP6 - Send batch to the server Completion ##

### Question/ description: ###
I'm facing an issue on eFlow 4.5 SP6 environment where only one user can send batched to the server during completion on a client machine.
If the customer use another user we got the following error.

    no sufficient Permissione: Stack Trace:
    as TiS.Core.Workflow.WFEngine.MsSql.SQLWFEngine.Throwconnectivity.Exception 

any hint would be appreciate.

### Answer: ###
Did you check if all the user have logon right to the _workflow DB

The eFlow user? yes he have but not the windows user.
I have one user that are definite as WFDBuser on the cab.
Any other ideas?