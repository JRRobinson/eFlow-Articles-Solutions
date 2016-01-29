# **Copy field in a table and link ROIs to correct page** #

## **Question / Description** ##

I want to copy the fields linked to a page to a table(one row for each page in a batch) but I am facing troubles linking the ROI to the correct page when the collection has more than one.
 
 
This is the code that I am calling, probably I am calling the AddFieldLink in a bad way:
 
   private void CopyFieldRoiAndConfidence(ValidationField vFSrc, ValidationField vFTarget)
        {
            if (vFSrc.eFField.FieldTop != 0 || vFSrc.eFField.FieldBottom != 0 || vFSrc.eFField.FieldLeft != 0 || vFSrc.eFField.FieldRight != 0)
            {
                // copy ROI
                vFTarget.eFField.FieldTop = vFSrc.eFField.FieldTop;
                vFTarget.eFField.FieldBottom = vFSrc.eFField.FieldBottom;
                vFTarget.eFField.FieldLeft = vFSrc.eFField.FieldLeft;
                vFTarget.eFField.FieldRight = vFSrc.eFField.FieldRight;
                //vFTarget.eFField.SourcePageOrderInCollection = vFSrc.eFField.ParentPage.OrderInCollection;
                vFSrc.eFField.ParentPage.AddFieldLink(vFTarget.eFField);
                
            }
            vFTarget.eFField.Confidence = vFSrc.eFField.Confidence;
        }
 
 
Indeed even after the exectution of this method vFSrc.eFField.ParentPage (page 2) is different from vFTarget.eFField (page 1):

![](http://i.imgur.com/KjOWtqw.png)


This is the piece of code where I build the table and call the function that copies the ROI:
 
 
for (short i = 0; i < collection.NumberOfPages; i++)
                {
                    ITisPageData page = collection.get_PageByIndex(i);
                    if(!page.IsAttachment)
                    table.AddRepetition();
                    foreach (ITisFieldArrayData array in table.FieldArrays)
                    {
                        string fieldPattern = regex.Replace(array.Name, replacement);
                        string fieldName = fieldPattern;
                        ITisFieldData field = page.get_LinkedField(fieldName);
                        if (field == null)
                        {
                         
                            throw new Exception(String.Format("The Field for the field [{0}]] is null.", field.Name));
                        }
 
                        ValidationField vF = validations.GetValidationField(csm, field);
                        if (vF == null)
                        {
                            throw new Exception(String.Format("The ValidationField for the field [{0}]] is null.", field.Name));
                        }
 
                        vF.Normalize();
                        if (vF.EfContent != String.Empty)
                        {
                            ITisFieldData tableField = array.get_LinkedFieldByIndex((short)(table.NumberOfRepetitions - 1));
                            //ITisFieldData tableField = array.get_LinkedFieldByIndex((short)(i));
                            ValidationField vFTable = validations.GetValidationField(csm, tableField);
                            if (vFTable == null)
                            {
                                throw new Exception(String.Format("The ValidationField for the table field [{0}]] is null.", tableField.Name));
                            }
                            
                            vFTable.EfContent = vF.EfContent;
                            //validations.CopyFieldBeforeNormalization(csm, vFTable);
                            vFTable.Normalize();
                            vFTable.eFField.Contents = vF.EfContent;
                            CopyFieldRoiAndConfidence(vF, vFTable);
                        }
                    }
 
 
 
Additional note: if I set the parent page using the statement commented (//vFTarget.eFField.SourcePageOrderInCollection = vFSrc.eFField.ParentPage.OrderInCollection;) I get the following error in completion:

![](http://i.imgur.com/zdwVY9d.png)


## **Answer / Solution** ##

I think that
oField.SourcePageOrderInCollection is the key.
 
It should probably be 0..pages-1 – maybe you’re assigning 1..pages
 
Try with hardcoded value, e.g 2 with 4-pages document, see what happens











