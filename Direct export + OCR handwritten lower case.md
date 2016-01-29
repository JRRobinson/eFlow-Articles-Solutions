# **Direct export + OCR handwritten lower case** #

## **Question / Description** ##

I am supporting a partner and I hope you can help me covering my lacks of knowledge.

This is the application workflow they are working on (handwritten forms):

![](http://i.imgur.com/7MrsEG5.jpg)


1)	 is it possible to configure eFLOW to route collections directly to Export when all the fields are valid? I know this is possible in IR, not sure I can achieve that without coding in “pure” eFLOW.

2)	Usually who compiles these forms writes the email address with lower case. Of course this adds complexity and I guess we cannot guarantee high recognition rates for this field. By the way I would like to know if any of you knows some good OCR configuration for a virtual engine to achieve the best results in this case (language is italian).

![](http://i.imgur.com/q9N8rFq.png)

Above a sample of what they want to capture. They used 2 eFlow fields, fEmail and fDomain to recognize it (fEmail@fDomain).



## **Answer / Solution** ##

For the 1st question there is a solution but custom code involved . 

You will need to implemented the following  code calling it from  PrePutCollection event . The function will loop on all fields in the collection and check if any of them don't pass validation .

In case the function return false, set collection.nextStation ="export"  otherwise set  it to "Completio".  You will also need to define the routing rules accordingly.
 
 
 
Here is function:
 
 
 
private bool isAllFieldsValid()
{
foreach (ITisCollectionData CollData in CSM.Dynamic.AvailableCollections)
{
    foreach (ITisFormData formData in CollData.Forms)
    {
        foreach (ITisFieldData fieldData in formData.Fields)
        {
            bool fieldValid = isFieldsValid(fieldData);
                      
            if (!fieldValid)
            {
               var validation = (ITisDataLayerValidation)fieldData;
 
              validation.Validate(validation.ValidationPolicy);
               if ((validation.LastValidationsResult.FinalValidationsStatus  !=        TiS.Core.PlatformRuntime.Validation.ValidationStatus.Valid  ))
 
             return false;
            }
        }
     }
}

















