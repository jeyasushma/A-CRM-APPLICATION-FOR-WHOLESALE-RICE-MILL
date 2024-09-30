CRM Application for Wholesale Rice Mill
Project By: Yerukala Jeya Sushma
Email: jyerukal@gitam.in
Salesforce Developer Setup Guide
1. Creating a Developer Account
Sign Up for Developer Account:
Visit the Salesforce Developer Sign-Up page.
Fill in the following details:
First Name & Last Name: Yerukala Jeya Sushma
Email:jyerukal@gitam.in
Role: Developer
Company: Gitam Institute of Technology
Country: India
Postal Code: [Your PIN Code]
Username:jeyasushma@gitam.in
Click Sign Me Up.
Activate Your Account:
Check your email inbox for an activation email from Salesforce.
Click Verify Account.
Set a new password and answer a security question, then click Change Password.
You will be redirected to your Salesforce setup page.
2. Creating Custom Objects
Create Supplier Object:
Navigate to Object Manager from the setup page.
Click Create > Custom Object.
Enter the following:
Label Name: Supplier
Plural Label Name: Suppliers
Record Name: Supplier Name (Data Type: Text)
Check Allow Reports, Track Field History, and Allow Search.
Click Save.
Create Rice Mill Object:
Navigate to Object Manager.
Click Create > Custom Object.
Enter the following:
Label Name: Rice Mill
Plural Label Name: Rice Mills
Record Name: Auto Number
Display Format: rice-{000}
Starting Number: 1
Check Allow Reports, Track Field History, Allow Search.
Click Save.
Create Consumer Object:
Follow the same steps as above with the following details:
Label Name: Consumer
Plural Label Name: Consumers
Display Format: consumers-{000}
Starting Number: 1
Create Rice Details Object:
Follow the same steps as above with the following details:
Label Name: Rice Details
Plural Label Name: Rice Details
Display Format: rice-{000}
Starting Number: 1
3. Creating Custom Tabs
Create a Tab for the Supplier Object:
Go to the setup page.
Type Tabs in the Quick Find box.
Click Tabs > New (under Custom Object Tabs).
Select Supplier and choose a tab style.
Click Next (default profiles page) > Next (Add to Custom App) > Uncheck Include Tab.
Ensure Append tab to users' existing personal customizations is checked.
Click Save.
Create Tabs for Remaining Objects:
Follow the same steps as above for Rice Mill, Consumer, and Rice Details objects.
4. Creating a Lightning App
Create a Lightning App:
Go to the setup page.
Search for App Manager and select it.
Click New Lightning App.
Enter the app name as MY RICE and click Next.
Keep default settings on the App Options and Utility Items pages, then click Next.
Upload a related photo for the app.
Add Navigation Items: Supplier, Rice Mill, Consumer, Rice Details.
Click Next.
Add the System Administrator profile.
Click Save & Finish.
5. Creating Fields and Relationships
Create Number Field in Rice Details Object:
Go to the setup page.
Click Object Manager and edit the Rice Details object.
Click Fields & Relationships > New.
Select Number and click Next.
Enter:
Field Label: Rice Distributed
Length: 5
Click Next > Save.
Create Junction Object:
Edit the Rice Details object.
Click Fields & Relationships > New.
Select Master-Detail Relationship.
Select Supplier as the related object.
Enter Field Label as Supplier Name and click Save & New.
Repeat the steps and select Rice Mill as the related object.
Enter Field Label as Rice Mill 1 and click Save.
Create Master-Detail Relationship between Consumer and Rice Mill:
Edit the Consumer object.
Click Fields & Relationships > New.
Select Master-Detail Relationship.
Select Rice Mill as the related object.
Enter Field Label as Rice Mill Name and click Save.
Create Roll-Up Summary Fields:
Supplier Object:
Go to Object Manager > Supplier > Fields & Relationships > New.
Select Roll-Up Summary.
Enter Field Label as Sum of Rice Distributed.
Summarize Rice Details object, use SUM function for the Rice Distributed field.
Rice Mill Object:
Follow similar steps with Field Label as Rice Distributed to Shops.
Summarize Rice Details object.
Consumer Object:
Create a Number field with Field Label as Rice Taken by Shops.
6. Creating Cross-Object Formula Fields
Create Cross-Object Formula in Consumer Object:
Go to Object Manager > Consumer > Fields & Relationships > New.
Select Formula and click Next.
Enter:
Field Label: Amount Paid
Field Name: Amount_Paid
Return Type: Number
Formula:
markdown
Copy code
rice_taken_by_shops__c * rice_mill_name__r.rice_price_kg__c
Click Check Syntax and Save.
Create Formula Field in Consumer Object:
Go to Object Manager > Consumer > Fields & Relationships > New.
Select Formula and click Next.
Enter:
Field Label: Consumer Name
Field Name: Consumer_Name
Return Type: Text
Formula:
arduino
Copy code
First_Name__c + ' ' + Last_Name__c
Click Check Syntax and Save.
7. Creating Validation Rules
Create Validation Rule for Phone Number in Consumer Object:
Go to Object Manager > Consumer > Validation Rules > New.
Enter:
Rule Name: PhonenumberOrEmailBlankRule
Description: Phone number and email should not be blank.
Formula:
scss
Copy code
OR(ISBLANK(phone_number__c), ISBLANK(email__c))
Error Message: Please fill in your phone number.
Error Location: Top of Page.
Click Save.
8. Creating Page Layouts
Create Page Layout for Consumer Object:
Go to Object Manager > Consumer > Page Layouts > New.
Select the existing layout, name it Consumer Layout, and click Save.
Add sections:
Personal Details: Include fields First Name, Last Name, Consumer Name, Phone Number, Email, Rice Mill Name.
Rice Details: Include fields Rice Taken by Shop, Rice Type.
Receipt Details: Include fields Mode of Payment, Amount Paid.
Click Save.
9. Creating Profiles
Create Owner Profile:
Go to Setup > Profiles > Clone the Standard User profile.
Name it Owner and click Save.
Set Custom Object Permissions as required.
Create Employer Profile:
Go to Setup > Profiles > Clone the Standard Platform User profile.
Name it Employer and click Save.
Set Custom Object Permissions as required.
Create Worker Profile:
Go to Setup > Profiles > Clone the Standard Platform User profile.
Name it Worker and click Save.
Set Custom Object Permissions as required.
10. Creating Roles
Create Employer Role:
Go to Setup > Roles > Set Up Roles.
Add a role under Owner.
Enter Role Label as Employer.
Click Save.
Create Worker Role:
Go to Setup > Roles > Set Up Roles.
Add a role under Owner.
Enter Role Label as Worker.
Click Save.
11. Creating Users
Create Owner User:
Go to Setup > Users > New User.
Enter:
First Name: Vicky
Last Name: Y
Alias: VY
Email: [owner.email@domain.com]
Username: [owner.username@domain.com]
Nickname: VY
Role: Owner
Profile: Owner
Click Save.
Create Employer User:
Go to Setup > Users > New User.
Enter:
First Name: Ram
Last Name: Ram
Alias: RR
Email: [employer.email@domain.com]
Username: [employer.username@domain.com]
Nickname: RR
Role: Employer
Profile: Employer
Click Save.
Create Worker User:
Go to Setup > Users > New User.
Enter:
First Name: Ragu
Last Name: Raj
Alias: RRJ
Email: [worker.email@domain.com]
Username: [worker.username@domain.com]
Nickname: RRJ
Role: Worker
Profile: Worker
Click Save.
12. Creating Reports
Create Report for Rice Details:
Go to App Launcher and select Reports.
Click New Report.
Choose Rice Details as the report type.
Click Continue.
Add fields like Supplier Name, Rice Distributed, Rice Mill 1, Rice Type.
Add filters as needed (e.g., Date Range).
Click Save & Run, name it Rice Distribution Report, and click Save.
Create Report for Supplier and Rice Mill Summary:
Follow similar steps and select Supplier and Rice Mill objects.
Add fields like Supplier Name, Total Rice Distributed, Rice Mill 1.
Add filters and groupings.
Click Save & Run, name it Supplier and Rice Mill Summary, and click Save.
13. Creating Dashboards
Create Dashboard for Rice Distribution:
Go to App Launcher and select Dashboards.
Click New Dashboard.
Enter Dashboard Name as Rice Distribution Dashboard.
Select the folder to save and click Create.
Add components using the reports created:
Chart: Add a bar chart for Rice Distribution Report.
Gauge: Add a gauge for total rice distributed.
Click Save.
Create Dashboard for Supplier and Rice Mill Summary:
Follow similar steps and select the Supplier and Rice Mill Summary report.
Add components such as pie charts and bar graphs to visualize data.
Click Save.
14. Apex Code
Create Apex Trigger for Rice Details Object:
Go to Setup > Apex Triggers > New.
Enter the following code:
apex
Copy code
trigger consumerTrigger on consumer__c (after insert) {
    if(trigger.isAfter && trigger.isInsert) {
        ConsumerRecord.sendEmailNotification(trigger.new);
    }
}
Click Save.
Create Apex Class for Custom Logic:
Go to Setup > Apex Classes > New.
Enter the following code:
apex
Copy code
class ConsumerRecord {
    public static void sendEmailNotification (List<consumer__c> con){
        for(consumer__c c: con) {
            Messaging.SingleEmailMessage email = new Messaging.SingleEmailMessage();
            email.setToAddresses(new List<String>{c.email__c});
            email.setSubject('Welcome to our company');
            email.setPlainTextBody(
                'Dear ' + c.Name + ',\n\n' +
                'Welcome to MY RICE! You have been seen as a valuable customer to us. ' +
                'Please continue your journey with us while we provide you with high-quality resources.\n' +
                'We are proud to associate with valuable customers like you and look forward to ' +
                'collaborating with you by offering more exciting discounts or product offers.\n' +
                'Thank you for choosing us!\n\n'
            );
            Messaging.sendEmail(new List<Messaging.SingleEmailMessage>{email});
        }
    }
}
Click Save.
This setup guide will help configure roles, users, reports, dashboards, and custom Apex code for the CRM Application for Wholesale Rice Mill.
