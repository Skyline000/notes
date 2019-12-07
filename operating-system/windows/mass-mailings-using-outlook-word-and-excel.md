# Mass Mailings using Outlook, Word, and Excel

### Prepare the recipients list

* You should store all of the recipient's information in an Excel spreadsheet.
* The first row of the spreadsheet should contain column headings such as First Name, Last Name, and Email Address.
* Each recipient's email address must be in a column by itself without the full name, angle brackets, quote marks, or other special characters.
* Each recipient's information must be listed on a separate row.
* Row and column example with column headings:

  | **First** | **Last** | **Email** |
  | :--- | :--- | :--- |
  | Jane | Smith | jane.smith@gmail.com |
  | John | Doe | jdoe@yahoo.com |
  | Robert | Roe | bob@msn.com |

### Prepare the email message

1. Start Microsoft Word and begin a new blank document.
2. Switch to the **Mailings** ribbon.
3. Click on the **Start Mail Merge** menu and select the **E-Mail Messages** option.
4. Click on the **Select Recipients** menu and select the **Use Existing List** option.
5. Browse and select the Excel spreadsheet you created earlier, and then click on the **Open** button.
6. In the **Select Table**window, click on the name of the sheet that contains your recipient's information.
   1. If you have options for Sheet1, Sheet2, and Sheet3, the information is probably on Sheet1.
   2. If you entered column headings in the first row of your spreadsheet, make sure the **First row of data contains column headers** option is checked.
   3. Click on the **OK** button.
7. Compose the body of your message using Word:
   * You can switch back to the **Home** ribbon to add formatting including bold, italics, font colors, and headings.
   * Not all formatting will visible to all recipients. Outlook users will see most of the formatting. Web mail users will see bold, italics, and lists but not font styles or colors.
8. To customize the contents of your message with information from your spreadsheet:
   1. Position the cursor where you want to insert the data.
   2. Switch to the **Mailings** ribbon.
   3. Click on the **Insert Merge Field** menu and select the field containing the data you want to insert.
9. Save the body of the email message the same way you would save any other Word document.

### Send the email messages

1. Switch to the **Mailings** ribbon.
2. Click on the **Finish & Merge** menu and select the **Send E-Mail Messages** option.
3. From the **To** drop-down menu, select the field containing the email address of each recipient.
4. In the **Subject** text box, enter the subject line used for the email message.
5. From the **Mail format** drop-down menu, select the **HTML** option.
6. For the **Send records** radio button, select the **All** option.
7. Click on the **OK** button to send the messages.

{% hint style="info" %}
To change the sending email address on a mail merge in Word 2013 you will need to make some changes in your corresponding Outlook 2013 account first.

1. Add the email account you wish to send FROM to your Outlook account,

2. Set it as the default email by going to File/Account Settings/Account Settings and clicking on the email you want.

3. Click on Set as default - a check mark will appear next to the account.

4. Then go to File/Options and under the Mail Category/Send Options make sure that the "Always Use the Default Email to Send Messages" is checked off.

5. Save and Exit.

Word and Outlook will now use whatever is marked as the default email as the sending email address on a mail merge.
{% endhint %}

{% embed url="https://www.statelibraryofiowa.org/ld/q-s/silo/e-mail/outlook/email-merge" %}

{% embed url="https://answers.microsoft.com/en-us/msoffice/forum/msoffice\_outlook-mso\_windows8/how-to-change-the-senders-email-address-in-mail/86110d33-3330-45b3-a7d4-dc9a5cf2e528" %}



