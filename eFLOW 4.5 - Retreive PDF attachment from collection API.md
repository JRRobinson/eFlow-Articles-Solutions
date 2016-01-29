# **eFLOW 4.5 - Retreive PDF attachment from collection API ** #

## **Question / Description** ##

For an eFlow 4.5.1.7 project I´m using ePortal as import station and storing the original PDF as an attachment using ePortal features. Now I need to retrieve this PDF to export it. (FileName Usertag contains PDF file name)
 
Can anyone share API snippet to get the PDF file stored or point me to the right method to query it?


## **Answer / Solution** ##

Here the quick code snippet

string fileName = collection.get_NamedUserTags(App.Settings.Shared.Constants.NamedUserTags.FileName[""]);
string path = oCSM.PathLocator.get_Path("TIF");
string fullPath = System.IO.Path.Combine(path, fileName);
if (collection.AttachedFileManager.QueryAttachment(fileName))
{
    collection.AttachedFileManager.GetAttachment(fullPath);
}






























