# **eFlow 5.1 - Organize station not working as expected** #

## **Question / Description** ##

I will open a urgent case, but before that I would like to check if someone have some clue or workaround.

I have a batch with 47 pages, I have processed into a IntegraActivity and 46 pages had EFI match. So only one should require manualId.

When I open the organize station and get the collection, all pages appears like no EFI applied, but the EFI is applied for 46 of them, only one page it is not.

See below

![](http://i.imgur.com/JCU8QXm.jpg)



## **Answer / Solution** ##

I had to set TemplateName parameter of a page to be the same as PageId.

I did it by code (as I had some custom code anyway), but perhaps it’s possible to do it inside some activity in your XAML.

we have managed to solve this issue. 

I would like to thanks Ofer from Support also, who quickly replied  me with a hotfix for this issue, but unfortunately it did not help. Only adding the following code in OnPostGetCollections solved the issue:

        public void OnPostGetCollections (ITisClientServicesModule csm)
        {
            foreach( ITisCollectionData collData in csm.Dynamic.AvailableCollections)
            {
                foreach(ITisPageData pageData in collData.Pages)
                {
                    pageData.TemplateName = pageData.PageId;
                }
            }
        }
