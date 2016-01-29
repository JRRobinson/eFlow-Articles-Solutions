## eFlow 4.5 - Tracking events of DbSearch on Positions table##

### Question/ description: ###

- Project: Coolblue
- eFlow: 4.5.1.700
- IR: 4.5.2.226 

Is there a way to track from Completion Station when the Position row was filled using F9, maybe an event I could subscribe?

Why? I need to update a flag under RefDb so the line will queried again.

### Answer: ###

    IRValidations-> protected virtual void OnPostOverwriteDBSearchField(ITIsClientServicesModule oCSM, ITIsFormData oForm, ITIsFieldData oField, Tis.DevGER.Shared.Forms.ctrlDBSearch.DbSearchField[] items, DataRow drResult, String sUseTableExtension)