# **eFlow 5.1 SP1 - Moving inside a field** #

## **Question / Description** ##

In completion, if doing ‘OCR on the fly’, then the first character seems to be selected automatically (mark with blue) and then the arrows buttons (to move left and right inside the textbox) do not respond.

On the image, the first letter of the selected text is also marked with green. 

Even if you click again on the textbox or going out and back to the field, it still on this state. 

This is problematic when you want to change one letter in the text box. you need to move and select with the mouse…or clean the field and re-write manually 

•	This does NOT happen on FreedomDemo on the same machine.

•	There is no customization in this project that can cause such thing.

•	When typing the text manually (or selecting from a dropdown list), there is no such issue and you can move with the arrows freely.

•	In this project it happens on every field. 

Does someone has an idea what can cause this? 

![](http://i.imgur.com/H1Wzy7g.png)


## **Answer / Solution** ##

Check engines configurations, their weights (for segmentation and results).

Some of them may be 0 – change it to anything higher than 0.
