## eFlow 4.5 - Original TIF in the Completion station ##

### Question/ description: ###

Does anyone know how to make eFlow display ROIs in correct positions when using TIF image in the Completion?

I have them shifted (which makes sense as FormOut moves them during matching).

I don't wasn't to display reconstructed image but original TIF + ROIs in correct positions.

There is an adjustment happening for JPEGs (at least according to Reflector)

eFlow 4.5 SP4

### Answer: ###
TRM solution works like a charm.

You can create TRM file to get the shifted scale and then force them on your current ROI.
    
    [DllImport(@"C:\Progrm Files\TIS\eFlow4\Bin\trm.dll",EntryPoint="InitTrm")]
    public static extern void InitTrm(char[] TRMFileName, ref long ShiftX, ref long ShiftY, ref double Skew, ref double Scale);
    [DllImport(@"C:\Progrm Files\TIS\eFlow4\Bin\trm.dll",EntryPoint="GetPageRot")]
    public static extern int GetPageRot();

    public override void OnPrePutCollections(ITisClientServicesModule CSM, ref bool CanPut){
    	Int32 shiftX=0;
		Int32 shiftY=0;
		double skew=0;
		double scale=0;

		string workdir = CSM.PathLocator.get_path("TIF")
		foreach(ITisCollectionData collData in collData.Pages)
		{
			string sPage=pageData.OrderInBatch.ToString();
			sPage=sPage.PadLeft(4,'0');
			string trmName=workdir+collData.Name+"_P"+sPage+".TRM";

			int rc=InitTrm(trmName, ref shiftX, ref shiftY, ref  skew, ref scale);
			if(rc!+0)
				MessageBox.Show("error"+rc.ToString());

			int rot=GetPageRot();
			if(rot!=0)
				MessageBox.Show(rot.ToString());
		}
    }