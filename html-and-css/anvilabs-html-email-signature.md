# Сorporate HTML Signature in Apple Mail
## Instructions
1. In Apple Mail, go to `Preferences` > `Signatures` and create a signature with *"PLACEHOLDER"* text.
![](http://i64.tinypic.com/14k89l4.png)

2. Associate the placeholder signature with one of your email accounts by dragging its name from the second column in the `Preferences` > `Signatures` window to an email account in the first column.
![](http://i68.tinypic.com/2i9qtg4.png)

3. Close the `Preferences` window to save it, then quit Mail.app.

4. Download the "email-signature_template.html" file from the [repository](https://bitbucket.org/anvilabs/email-signature) and open it in your favorite text editor.

5. After opening the file, edit the following lines with appropriate personal information and leave this file open for a while:
```
...
<strong>NAME SURNAME</strong>
<!--INSERT REQUIRED NAME INSTEAD-->
...
<span style="color:black">PHONE NUMBER</span>
<!--INSERT REQUIRED PHONE NUMBER INSTEAD-->
...
<a href="mailto:USERNAME@anvilabs.co" target="_blank" style="display:inline-block; margin-right:2px;">
<!--INSERT REQUIRED USERNAME INSTEAD-->
...
<a href="mailto:USERNAME@anvilabs.co" target="_blank" style="text-decoration:none;">
<!--INSERT REQUIRED USERNAME INSTEAD-->
...
<span style="color:black">USERNAME@anvilabs.co</span>
<!--INSERT REQUIRED USERNAME INSTEAD-->
...
```

6. Open up the Terminal.app, found in `Applications` > `Utilities`, and insert one of the following commands.
  * Using the iCloud Drive:
```
cd ~/Library/Mobile\ Documents/com~apple~mail/Data/V3/MailData/Signatures/ && open -t "$(grep -il placeholder ubiquitous_*.mailsignature)"
```
  * Not Using iCloud Drive:
```
cd ~/Library/Mail/V3/MailData/Signatures/ && open -t "$(grep -il placeholder ubiquitous_*.mailsignature)"
```

7. When you created a temporary placeholder signature in step 1, Mail.app automatically created a ubiquitous_XXXXXXX.mailsignature file that represents it. This placeholder now should be open in default text editor.
![](http://i63.tinypic.com/fem5mp.png)
> Look for your placeholder text in the highlighted part shown in the image above. Here, we know we have the correct file because we can clearly see our placeholder text: “This is a placeholder.”.
If you cannot find the placeholder, you may still be in “edit” mode on the signature. Try closing the `Mail` > `Preferences` Window, quitting Apple Mail and opening the files using the process outlined in the previous step.
If you still cannot find the placeholder, you may need to try one of the other folders from the above step.

8. When you have located the right placeholder `.mailsignature` file, keep it open. You will see a few metadata lines on the top of the file and some html code below it. Select only the placeholder code as shown below.
![](http://i67.tinypic.com/2mq6cl0.png)

9. Keep the top metadata lines, but replace the html in the file with your own from step 5, i.e. from `<body>` to `</body>` tags.
![](http://i66.tinypic.com/j0y1bd.png)

10. Save and close the file.

11. **If you are using iCloud Drive, skip this step and proceed to the next step**. You can determine if you are using iCloud for Apple Mail by checking `System Preferences` > `iCloud`. Still unsure? Skip this step — you can redo the steps and include this one if your signature is not working correctly at the end.
Even though you save this file, Mail.app may use the original version and overwrite your new signature unless you lock the file. With your text editor now closed and the file saved, go back to terminal, enter the following line, and lock all the `mailsignature` files in the folder.
  * Lock files:
  ```
  chflags uchg ~/Library/Mail/V3/MailData/Signatures/*.mailsignature
  ```
  If you mess up, you can unlock the files with this command.

  * Unlock Files:
  ```
  chflags nouchg ~/Library/Mail/V3/MailData/Signatures/*.mailsignature
  ```

12. Open Mail.app and go back to `Preferences` > `Signatures`. If you have images in your signature, they will will not show here in the preview, but they will show in the real signature if the image source location is valid.
![](http://i65.tinypic.com/2d810nc.png)

13. To test that it is working correctly, simply compose a new email using the account you associated this signature with in step 2, and set the signature (right side of screen) to be the one with the name you created in step 1. If the images show, and everything looks as it should, you have succeeded!
![](http://i66.tinypic.com/erzq0w.png)

-----
# Credits
[How to Make an HTML Signature in Apple Mail for El Capitan OS X 10.11 by Matt Coneybeare](http://matt.coneybeare.me/how-to-make-an-html-signature-in-apple-mail-for-el-capitan-os-x-10-dot-11/)