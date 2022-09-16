# Microsoft Dynamics 365 (D365) CRM Missing Privilege Error

## Problem Statement:
When creating a batch of Task records in Microsoft Dynamics 365 (D365) CRM,  some records were successfully created and some records threw errors due to insufficient privilege.

**Error Message:**

[400] (0x80040299) Principal user (Id=xxxxxxx-xxxx-xxxx-xxxxxxxx), type=8, roleCount=1, privilegeCount=0, accessMode=0), is missing prvReadActivity privilege (Id=xxxxxxx-xxxx-xxxx-xxxxxxxx) on OTC=xxxx for entity 'activitypointer' (LocalizedName='Activity') in Business Unit: Business Unit (Id=xxxxxxx-xxxx-xxxx-xxxxxxxx). context.Caller=xxxxxxx-xxxx-xxxx-xxxxxxxx [HTTP/1.1 400 Bad Request]


## Troubleshooting:
**Step-1:** Find the user-names in successful and error records.

**Step-2:** Compare the successful user record with the erroneous user record in D365 CRM.

**Step-3:** The erroneous user record didn’t have any “Security Role" assigned to it, whereas, the successful user record had "Dynamics 365 App for Outlook User" and "Customer service app access" security roles. Upon further investigation, it was found out that only "Dynamics 365 App for Outlook User" had permission to the "Activity" entity.

![a1](https://user-images.githubusercontent.com/12267939/190628979-1cf7b5ff-eb96-40b6-8173-2719e0ff88f4.png)       

![a2](https://user-images.githubusercontent.com/12267939/190629008-80e30866-281b-43ec-8a3d-2089911ed31b.png)


## Resolution:
At least, assign the "Dynamics 365 App for Outlook User" security role to the affected user, and ensure the user has the required granular level of access to the concerned object(s) in this security role.
![a3](https://user-images.githubusercontent.com/12267939/190629058-d53ba125-3aaf-43df-bd82-65d277a23262.png)
