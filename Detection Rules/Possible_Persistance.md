# Possible Persistance IOC

## Alert Name: *User Account Created*

## Description
- Fires an alert if a user is created 

## Data Source & Identifiers
- Windows EventCode: 4720

### SPL Query:
`index=* EventCode=4720 | table _time, Subject_Account_Name, New_Account_Account_Name, host | rename New_Account_Account_Name as "New User", Subject_Account_Name as "Creator"`

- The `table` is used to display the information for a SOC Analyst.
- The `rename` is used to transform the table into a more readable format to show *who was added* & *who added the user*.

# Alert Being Triggered: 

<img width="2557" height="252" alt="image" src="https://github.com/user-attachments/assets/b1b46d22-7c25-44ba-bda4-5d28f4d09b26" />

## Viewed Result:

<img width="2552" height="375" alt="image" src="https://github.com/user-attachments/assets/d82c85e2-5ebb-4c5c-a22b-5d3ccbfb2cf8" />

# False Positives:
- IT is provisioning a domain account for this user.
- IT was creating a local admin account for a management approved developer.


