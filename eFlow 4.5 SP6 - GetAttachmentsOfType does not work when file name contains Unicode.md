# **eFlow 4.5 SP6 - GetAttachmentsOfType does not work when file name contains Unicode ** #

## **Question / Description** ##

I found that when using the following query:

oCollData.AttachedFileManager.GetAttachmentsOfType(".pdf", sWorkDir);

The attachments are not fetched when they contains Unicode characters like the following example: N-FACTURA Nº 17939.pdf

Does anyone have a workaround?

For this application the attachment file names are unknown but the extension which always would be pdf.



## **Answer / Solution** ##

There was issue in the past with non-standard characters and for these reasons a Replace functionality exists in ePortal.

Add your character and the problem will be gone.
Note: the magic symbol (?-i) makes sure that the match is case-sensitive

      <RenameAttachment Enabled="true" Replaces="(?:[\.](?![^\.]+$))=_|(?-i)[ąä]=a|(?-i)[ĄÄ]=A|(?-i)[ć]=c|(?-i)[Ć]=C|(?-i)[ę]=e|(?-i)[Ę]=E|(?-i)[ł]=l|(?-i)[Ł]=L|(?-i)[ń]=n|(?-i)[Ń]=N|(?-i)[óö]=o|(?-i)[ÓÖ]=O|(?-i)[ś]=s|(?-i)[Ś]=S|(?-i)[ß]=ss|(?-i)[ü]=u|(?-i)[Ü]=U|(?-i)[źż]=z|(?-i)[ŹŻ]=Z" Description="Rename attachments with IR-like Replaces syntax" />
    </CollectionCreation>

To be safe - you may try to replace all non-unicode characters with underscore.

According to this link http://stackoverflow.com/questions/3203190/regex-any-ascii-character  this should look like below

      <RenameAttachment Enabled="true" Replaces="(?:[\.](?![^\.]+$))=_|(?-i)[ąä]=a|(?-i)[ĄÄ]=A|(?-i)[ć]=c|(?-i)[Ć]=C|(?-i)[ę]=e|(?-i)[Ę]=E|(?-i)[ł]=l|(?-i)[Ł]=L|(?-i)[ń]=n|(?-i)[Ń]=N|(?-i)[óö]=o|(?-i)[ÓÖ]=O|(?-i)[ś]=s|(?-i)[Ś]=S|(?-i)[ß]=ss|(?-i)[ü]=u|(?-i)[Ü]=U|(?-i)[źż]=z|(?-i)[ŹŻ]=Z|[^\x00-\x7F]=_" Description="Rename attachments with IR-like Replaces syntax" />
























