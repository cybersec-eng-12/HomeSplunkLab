# Possible Brute Force Attack

## Alert Name: *Multiple Failed Login Attempts*

## Description
- Detects if user has failed to input their password correctly > 3 times.

## Data Source & Identifiers
- Windows EventCode: 4625.

### SPL Query:
`index=* EventCode=4625
| stats count by host, user
| where count > 3`

- The `stats` command is to count the amount of times a user on a specific host failed to enter their password correctly. 
- The `where` command filters all results that are <= 3.

# Alert Being Triggered: 

<img width="2549" height="252" alt="brute_force_alert_being_triggered" src="https://github.com/user-attachments/assets/1c558562-5921-46da-ae50-a88598ced304" />

## Viewed Result:

<img width="2558" height="412" alt="image" src="https://github.com/user-attachments/assets/3110dce7-6d66-46fe-9c81-cc45685da47a" />

# False Positives:
- User was legitmately trying to gain access but they forgot their password.

