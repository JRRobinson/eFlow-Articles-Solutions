# **Capture delete event in the Controller** #

## **Question / Description** ##

Anybody knows if (and how) it’s possible to capture the delete event in the controller to modify its behavior?


## **Answer / Solution** ##

You can code:
 
 
Do a class controller
 
public class ControllerEvents : TiS.Core.eFlowAPI.Events.EventsAdapterController
 
{
 
 
 
public override void OnPreManageCollections(ITisClientServicesModule oCSM, ITisManageCollectionAction oAction, ref bool bCanDoAction, ref bool bDetailsNeeded)

{
I             if (oAction.ManageCollectionAction == TIS_MANAGE_COLLECTION_ACTION.DELETE)
             {
                    {
                       MessageBox.Show("Action denied, delete batches is not allowed.", "Warning", MessageBoxButtons.OK, MessageBoxIcon.Exclamation);
                        bCanDoAction = false;
              }
 
}
 
To get more details use the event:
 
public override void OnManageCollectionsDetails(ITisClientServicesModule oCSM, ITisManageCollectionAction oAction, ITisManageCollectionActionInfo oCollectionActionInfo, ref bool bCanDoAction)








