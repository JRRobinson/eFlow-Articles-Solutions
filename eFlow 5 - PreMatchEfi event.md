# **eFlow 5 - PreMatchEfi event** #

## **Question / Description** ##

I need some help with eFlow 5 recognition events.

I have an old code (eF4.5) which is selecting specific EFI list depending on barcode for page. It was done in FormId of course.

Now, in eF5, I would need to do the same in Integra Activity. 

I know there is a PreMatchEfi event there, but I have no idea how to use it and where to find override for it.

Anyone having a sample code for this event?





## **Answer / Solution** ##

So I got some answers and a solution (credits to Ben and Yuval, in alphabetical order ;) )

Yuval suggested to use Recognition workflow and gave this example (have not tested it yet, but I believe it should work):

![](http://i.imgur.com/ZGxCwyP.jpg)

While Ben has presented custom code approach (‘TiS.IntegraService.dll’ is required in your solution):

using TiS.RecognitionServices.IntegraService;

        public void OnPrePage(Object sender, PrePageEventArgs e)
        {
            if (_coll != null)
            { 
                _currentPage = _coll.Pages.GetByIndex(e.PageIndex);
                pageBarcode = string.Empty;
                if (!string.IsNullOrEmpty(_currentPage.GetNamedUserTags(Const.UserTag.PageNo)) && _currentPage.GetNamedUserTags(Const.UserTag.PageNo).Length>3)
                {
                    pageBarcode = _currentPage.GetNamedUserTags(Const.UserTag.PageNo).Substring(0,4);
                }
            }
        }

        public void OnPreMatchEfi(Object sender, PreMatchEFIEventArgs e)
        {
            if (_currentPage != null)
            {
                if (!e.NextEFI.StartsWith(pageBarcode))
                { e.SkipNextEFI = true; }
                else
                { e.SkipNextEFI = false; }
            }
        }

And of course you have to get _coll in OnPostGetcollections 








