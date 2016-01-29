## eFlow 4.5 - field validation ##

### Question/ description: ###

in the Completion station filled fields are not recognised. Some have code attached to these fields and the problem here is that the code is not working.

How can I set the field validation in completion station to unknown?


### Answer: ###
This code must be attached to the field:

    #region ForceFieldValidation(int iFormNum, string sFieldGroupName, string sFieldName)
    
    ///<summary>
	///This is to force the field validation(vFunction) to be re-triggered. This is useful for inter-field validation.
	///</summary>
	///<param name="iFormNum">The actual physical form count number</param>
	///<param name="sFieldGroupName">The actual field group name defined in visual designer</param>
	///<param name="sFieldName">The actual field name defined in visual designer</param>
	public static void ForceFieldValidation(int iFormNum, string sFieldGroupName, string sFieldName)
	{
		IStationAccess station=StationCreator.SingletonInstance;
		string sFormName=TiS.AP.CPS.Common.Formattin.FormatUtils.ConvertFormNumToFormDataName(iFormNum);

		foreach(TiS.DataEntry.DataAccess.Interfaces.IDataForm formData in station.State.Batch.Forms)
		{
			if(formData.Name==sFormName)
			{
				foreach(TiS.DataEntry.DataAccess.Interfaces.IDataGroup dataGrp in  station.State.Form.Groups)
				{
					if(dataGrp.Name==sFieldGroupName)
					{
						foreach(TiS.DataEntry.DataAccess.Interfaces.IDataField dataField in dataGrp.Fields)
						{
							if(dataField.Name==sFieldName)
							{
									dataField.ValidStatus=TiS.DataEntry.DataAccess.Interfaces.ValidStatus.Unknown;
							break;

							}
						}
						break;
					}
					break;
				}
			}
		}
		#endregion