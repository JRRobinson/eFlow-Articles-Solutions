# **Accessing to the FinalDRD from the station events** #

## **Question / Description** ##

is it possible to access to the finalDRD object by code OnPrePutCollection?

I need to copy the content and ROIs of the fields recognized by applying the same integra form to an undetermined number of pages to a table in order to display it nicely in completion.

If it is possible, any sample code on how to access this object would be appreciated.



## **Answer / Solution** ##

The solution to this: the highlighted part is the core function that builds the DRD class object out from the DRD attachment to the collection. 

This function is taken by Nir’s magic TiS.Engineering.Generics, thanks Shay for pointing me to this.

public static List<IPageRecognition> GetDrdPageRecognition(string drdPath, bool changedPagesOnly)

        {
            List<IPageRecognition> result = new List<IPageRecognition>();
            try
            {
                using (StreamReader sr = new StreamReader(drdPath))
                {
                    TiS.RecognitionServices.IDocumentRecognition idc = TiS.RecognitionServices.Helpers.Persistence.ReadDocumentFrom(sr.BaseStream);
                    if (idc != null && idc.RecognitionPages != null)
                    {
                        foreach (IPageRecognition ipg in idc.RecognitionPages)
                        {
                            if (!changedPagesOnly || (ipg.Transform.Rotation != 0f || ipg.Transform.Shift != SizeF.Empty || ipg.Transform.Skew != PointF.Empty))
                            {
                                result.Add(ipg);
                            }
                        }
                    }
                }
            }
            catch (Exception ex)
            {
                ILog.LogError(ex);
            }
            return result;
        }
        #endregion





