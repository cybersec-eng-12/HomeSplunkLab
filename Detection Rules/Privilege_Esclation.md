# Privilge Esclation IOC

## Alert Name: *User Added to Domain Admins*

## Description
- Fires an alert if a user is added to a Global, Local, or Universal group where the name is "Domain Admins".

## Data Source & Identifiers
- Windows EventCodes: 4728(Global) OR 4732(Local) OR 4756(Uniserval).
- Group_Name is "Domain Admins".

### SPL Query:
`index=* (EventCode=4728 OR EventCode=4732 OR EventCode=4756) Group_Name="Domain Admins" | table _time, host, Group_Name, user, Subject_Account_Name | rename Subject_Account_Name as "Added by", user as "User added to Group"`

- The `table` is used to display the information for a SOC Analyst.
- The `rename` is used to transform the table into a more readable format to show *who added the user* & *who was added* to the SOC Analyst.

# Alert Being Triggered: 

<img width="2539" height="258" alt="image" src="https://github.com/user-attachments/assets/82f45c96-0be2-469b-b2a7-5edfe21909ef" />

## Viewed Result:

<img width="2556" height="369" alt="image" src="https://github.com/user-attachments/assets/8321dbaa-8e70-4b00-a2da-0988a07abb04" />

# False Positives:
- New hire within IT domain management was added to this group apart of the on-boarding process. 

