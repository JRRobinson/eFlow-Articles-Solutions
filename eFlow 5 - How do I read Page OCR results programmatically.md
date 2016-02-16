## eFlow 5 - How do I read Page OCR results programmatically ##

### Question/ description: ###
Need to obtain data from PageOCR through custom code.

### Answer: ###
Can be done by reading PRD content created by PageOCR, using TiS.Recognition.Common.dll

Code sample:

    using TiS.Recognition.Common;
    
    TPage page= TPage.LoadFromPRD("Your PRD file");
    foreach (TLine word in page.Lines)
    {
    	foreach (TWord word in line.Words)
    	{
    		//processing all words in current line
    	}
    	//processing all lines in current page
    }