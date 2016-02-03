# **eFlow 5 - TAB  key event** #

## **Question / Description** ##

My client wants to prevent the Tab key on last field in completion to submit the form.

For that , I’d like to be able to catch  the Tab key event  to  cancel the field exit.

I’ve  overridden the on key event but it doesn’t get triggered on tab press.

Eflow 5.0.2.2


## **Answer / Solution** ##

In the past, I’ve blocked the controller from allowing the user from right clicking  and allowing the user from seeing the tif image of a collection.

I did this by processing windows messages, so I think you can do the same, in Completion, but it needs to be tried/adjusted.
 
In order to start filtering, simply hook it during on login event of your completion project.

You can also create your own events, like on TABEntered or something like that…
 
public override void OnLogin(ITisClientServicesModule oCSM)
{
 
btn = new ButtonHandler();
btn.ViewCollectionClicked += new EventHandler(btn_ViewCollectionClicked);
Application.AddMessageFilter(btn);
}














